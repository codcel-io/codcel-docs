<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# CI/CD Pipelines

The [Codcel CLI](./cli.md) runs unattended, so code can be regenerated automatically whenever a
workbook changes — and built and tested in the same pipeline.

Every pipeline needs the same three things:

1. **An API token** stored as a secret named `CODCEL_TOKEN`. Create it under
   **Account → API tokens** in your Codcel account; see [API Tokens](./api-tokens.md).
2. **The CLI**, from the install script or the `ghcr.io/codcel-io/codcel` Docker image.
3. **A `codcel generate` step**, preferably with `--require-auth` (fail if the secret is
   missing) and `--max-credits` (cap spending).

In the examples, replace `X.Y.Z` with the CLI version you have tested. Pinning a version keeps
generated code identical between runs; upgrade deliberately.

---

## GitHub Actions

Add the token as a repository or organization secret named `CODCEL_TOKEN`
(**Settings → Secrets and variables → Actions**).

```yaml
# .github/workflows/codcel.yml
name: Generate code from Excel

on:
  push:
    paths: ["specs/**.xlsx", "codcel.toml"]
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install the Codcel CLI
        run: |
          curl -fsSL https://codcel.io/install.sh | CODCEL_VERSION=X.Y.Z sh
          echo "$HOME/.local/bin" >> "$GITHUB_PATH"

      - name: Generate
        env:
          CODCEL_TOKEN: ${{ secrets.CODCEL_TOKEN }}
        run: >
          codcel generate specs/model.xlsx
          --targets python,typescript-client
          --require-auth --max-credits 300
          --output-format json > codcel-result.json

      - name: Test the generated Rust library
        run: cargo test --release
        working-directory: codcel-output/model/model-calculation

      - uses: actions/upload-artifact@v4
        with:
          name: generated-code
          path: |
            codcel-output/
            codcel-result.json
```

Running the job in the Docker image instead of installing:

```yaml
jobs:
  generate:
    runs-on: ubuntu-latest
    container: ghcr.io/codcel-io/codcel:X.Y.Z
    steps:
      - uses: actions/checkout@v4
      - run: codcel generate specs/model.xlsx --targets java --require-auth
        env:
          CODCEL_TOKEN: ${{ secrets.CODCEL_TOKEN }}
```

!!! note "Pull requests from forks"
    GitHub does not pass secrets to workflows triggered by pull requests from forks. Such runs
    have no `CODCEL_TOKEN`; with `--require-auth` they fail clearly instead of generating
    Non-Commercial code.

---

## GitLab CI/CD

Add `CODCEL_TOKEN` under **Settings → CI/CD → Variables**, with *Mask variable* and, if the job
only runs on protected branches, *Protect variable* enabled.

```yaml
# .gitlab-ci.yml
generate:
  image:
    name: ghcr.io/codcel-io/codcel:X.Y.Z
    entrypoint: [""]        # the image's entrypoint is `codcel`; let GitLab run its shell
  rules:
    - changes: ["specs/*.xlsx", "codcel.toml"]
  script:
    - codcel generate specs/model.xlsx --targets go-server --require-auth --max-credits 300
  artifacts:
    paths: [codcel-output/]
```

---

## Azure DevOps

Add `CODCEL_TOKEN` as a secret pipeline variable (or in a variable group). Azure DevOps does not
expose secret variables to scripts automatically, so map it with `env:`.

```yaml
# azure-pipelines.yml
trigger:
  paths:
    include: ["specs/*.xlsx"]

pool:
  vmImage: ubuntu-latest

steps:
  - script: |
      curl -fsSL https://codcel.io/install.sh | CODCEL_VERSION=X.Y.Z sh
      echo "##vso[task.prependpath]$HOME/.local/bin"
    displayName: Install the Codcel CLI

  - script: codcel generate specs/model.xlsx --targets csharp-server --require-auth --max-credits 300
    displayName: Generate
    env:
      CODCEL_TOKEN: $(CODCEL_TOKEN)

  - publish: codcel-output
    artifact: generated-code
```

On Windows agents, install with PowerShell instead:

```yaml
  - powershell: |
      $env:CODCEL_VERSION = "X.Y.Z"
      irm https://codcel.io/install.ps1 | iex
      Write-Host "##vso[task.prependpath]$env:LOCALAPPDATA\Programs\codcel"
    displayName: Install the Codcel CLI
```

---

## Jenkins

Store the token as a *Secret text* credential, here with the id `codcel-token`.

```groovy
// Jenkinsfile
pipeline {
  agent { docker { image 'ghcr.io/codcel-io/codcel:X.Y.Z'; args '--entrypoint=' } }
  stages {
    stage('Generate') {
      steps {
        withCredentials([string(credentialsId: 'codcel-token', variable: 'CODCEL_TOKEN')]) {
          sh 'codcel generate specs/model.xlsx --targets java-server --require-auth --max-credits 300'
        }
      }
    }
  }
  post {
    success { archiveArtifacts artifacts: 'codcel-output/**' }
  }
}
```

---

## Bitbucket Pipelines

Add `CODCEL_TOKEN` as a *Secured* repository variable; Bitbucket exposes it to the build as an
environment variable.

```yaml
# bitbucket-pipelines.yml
image: ghcr.io/codcel-io/codcel:X.Y.Z

pipelines:
  default:
    - step:
        name: Generate
        script:
          - codcel generate specs/model.xlsx --targets python --require-auth --max-credits 300
        artifacts:
          - codcel-output/**
```

---

## Any CI system with Docker

```bash
docker run --rm \
  -e CODCEL_TOKEN \
  -u "$(id -u):$(id -g)" \
  -v "$PWD:/work" \
  ghcr.io/codcel-io/codcel:X.Y.Z \
  generate specs/model.xlsx --targets python --require-auth
```

`-e CODCEL_TOKEN` passes the variable from the calling environment without writing its value on
the command line, and `-u` makes the generated files belong to you rather than to `root`.

With Docker secrets or Kubernetes, mount the token as a file and use `--token-file`:

```bash
codcel generate specs/model.xlsx --token-file /run/secrets/codcel_token --require-auth
```

---

## Using a project file

Keeping options in a `codcel.toml` next to the workbook makes the pipeline step trivial and keeps
the configuration under review like any other code. A project created in the desktop app works
as is:

```bash
codcel generate --config codcel.toml --require-auth
```

See [Project Files](./cli.md#project-files).

---

## Reacting to the result

| Exit code | Meaning | Typical pipeline action |
|-----------|---------|-------------------------|
| `0` | Success | Continue |
| `3` | Credentials missing, invalid, expired or revoked | Fix the `CODCEL_TOKEN` secret |
| `4` | Not enough credits, or over `--max-credits` | Top up credits or raise the limit |
| `5` | Codcel API unreachable, or this CLI version is retired | Retry later / upgrade the CLI |
| `6` | Transpiler errors (or warnings with `--fail-on-warnings`) | Fix the workbook cells listed in the log |

With `--output-format json`, the summary on standard output includes the credits spent, the
remaining balance and every compiler message, ready for a pipeline to report on. See
[JSON output](./cli.md#json-output).

---

## Network requirements

The CLI connects over HTTPS to `codcel-api-prod.fly.dev` to check credentials and spend credits.
Behind a proxy, set `HTTPS_PROXY`. Installing additionally needs `codcel.io`, `github.com` and
`objects.githubusercontent.com`, or `ghcr.io` for the Docker image.
