<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# API Tokens

An API token lets the [Codcel CLI](./cli.md) generate commercially licensed code without anyone
signing in — in CI/CD pipelines, on build servers and in scheduled jobs. A token works like a
password for your organization: whoever has it can generate code and spend the organization's
credits.

---

## Creating a token

1. Sign in at [codcel.io](https://codcel.io) as an organization owner and open **Account → API tokens**.
2. Enter a name that says where the token will be used, for example
   `GitHub Actions – loan-model`.
3. Choose when it expires: 30, 90, 180 or 365 days, or never.
4. Select **Create** and copy the token.

The token is shown **once**. Codcel stores only a one-way hash of it, so it cannot be displayed
again. If you lose it, revoke it and create a new one.

Tokens look like `codcel_pat_…` followed by 49 letters and digits. The last six characters are a
checksum, so the CLI recognises a mistyped or truncated token immediately and says so.

---

## Using a token

Give the token to the CLI in the `CODCEL_TOKEN` environment variable, from your CI system's
secret store:

```bash
CODCEL_TOKEN=codcel_pat_… codcel generate model.xlsx --require-auth
```

Alternatives:

- `--token-file /run/secrets/codcel_token` (or `CODCEL_TOKEN_FILE`) reads it from a file, which
  suits Docker and Kubernetes secrets.
- `codcel login --with-token` saves it on a machine, reading the token from standard input.

Check what a token resolves to with:

```bash
codcel auth status
```

See [CI/CD Pipelines](./ci-cd.md) for complete pipeline configurations.

---

## Managing tokens

**Account → API tokens** lists each token's name, the beginning of its value (`codcel_pat_a1B2c3D4…`),
who created it, when it was last used and when it expires. Owners see every token in the
organization.

- **Revoke** a token to disable it. It stops working immediately, including in pipeline runs that
  are already in progress — such a run fails without producing output and without spending
  credits.
- Removing a member from the organization also disables every token that member created.
- Expired and revoked tokens stay in the list for 30 days so you can see what happened.
- **Account → Credit usage** shows each run with the name of the token that made it.

To **rotate** a token: create a new one, update the secret in your CI system, run the pipeline
once, then revoke the old token.

---

## Security recommendations

- **One token per pipeline or project.** A leaked token can then be revoked without affecting
  anything else, and credit usage shows exactly where spending comes from.
- **Set an expiry date** and rotate before it passes. Use tokens that never expire only where
  rotation is impractical.
- **Never commit a token** to a repository, and don't pass it as a command-line argument — use
  your CI system's secrets and the `CODCEL_TOKEN` variable. CI systems mask secrets in logs; the
  CLI itself never prints a token, only its first characters.
- **Limit spending** with `--max-credits` so a misconfigured pipeline cannot use up the
  organization's balance.
- **Use `--require-auth`** so a missing secret fails the build instead of silently generating
  Non-Commercial code.
- If a token may have leaked, **revoke it first**, then create a replacement.

---

## Tokens or `codcel login`?

| | API token | `codcel login` |
|---|---|---|
| Intended for | Pipelines, servers, scheduled jobs | Your own computer |
| Sign-in | None — the token is the credential | Email link |
| Stored | In your CI system's secrets | OS keychain (Linux: a file only you can read) |
| Organization | Fixed to the organization it was created in | Chosen at sign-in, or `--org` per run |
| Revocation | Account → API tokens | `codcel logout` |
