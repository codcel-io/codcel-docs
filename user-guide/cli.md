<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Command Line Interface

The `codcel` command line interface (CLI) generates code from Excel workbooks without the desktop
app. Every option of the desktop app is available, so the CLI can run unattended in scripts and
CI/CD pipelines. It also generates code faster than the desktop app.

```bash
codcel generate model.xlsx --targets python,typescript-client
```

!!! tip "Running in CI/CD?"
    See [CI/CD Pipelines](./ci-cd.md) for ready-to-use GitHub Actions, GitLab CI, Azure DevOps,
    Jenkins and Bitbucket configurations.

---

## Installation

All installation methods download the same signed release binaries.

=== "macOS / Linux"

    ```bash
    curl -fsSL https://codcel.io/install.sh | sh
    ```

    Installs the latest release into `~/.local/bin` (or `/usr/local/bin` when run as root).
    Choose a version or location with environment variables:

    ```bash
    curl -fsSL https://codcel.io/install.sh | CODCEL_VERSION=0.2.0 CODCEL_INSTALL_DIR=/opt/bin sh
    ```

=== "Windows (PowerShell)"

    ```powershell
    irm https://codcel.io/install.ps1 | iex
    ```

    Installs into `%LOCALAPPDATA%\Programs\codcel` and adds it to your user `PATH`. Set
    `$env:CODCEL_VERSION` first to install a specific version.

=== "Homebrew"

    ```bash
    brew install codcel-io/tap/codcel
    brew upgrade codcel        # later, to update
    ```

=== "Docker"

    ```bash
    docker run --rm -u "$(id -u):$(id -g)" -v "$PWD:/work" ghcr.io/codcel-io/codcel generate model.xlsx
    ```

    Images are published for `linux/amd64` and `linux/arm64`, tagged with each version and `latest`.

=== "Manual download"

    Download the archive for your platform from the
    [releases page](https://github.com/codcel-io/codcel-cli/releases), check it against
    `SHA256SUMS`, and put the `codcel` binary on your `PATH`.

| Platform | Architectures |
|----------|---------------|
| macOS | Apple silicon (arm64), Intel (x86_64) — signed and notarized |
| Linux | x86_64, arm64 — static binaries, no system libraries needed |
| Windows | x86_64 |

Check the installation:

```bash
codcel --version
```

!!! note "Pin versions in pipelines"
    `latest` is convenient on a workstation. In CI, install a fixed version (`CODCEL_VERSION=…`
    or the `ghcr.io/codcel-io/codcel:<version>` image) so a new release never changes your
    generated code unexpectedly.

---

## Quick Start

```bash
# 1. Generate the Rust calculation library (free, Non-Commercial license notice)
codcel generate model.xlsx

# 2. Sign in to generate commercially licensed code with your organization's credits
codcel login

# 3. See the targets and what they cost
codcel targets

# 4. Preview a run, then run it
codcel generate model.xlsx --targets python,java-server --dry-run
codcel generate model.xlsx --targets python,java-server
```

The generated project is written to `./codcel-output/<project>/`, where the project name defaults
to the workbook's file name.

---

## Commands

| Command | Description |
|---------|-------------|
| `codcel generate` | Generate code from an Excel workbook |
| `codcel targets` | List the available targets, their dependencies and credit prices |
| `codcel detect-io` | Review the workbook's inputs and outputs and save the selection to `codcel-io.toml` |
| `codcel credits` | Show the credit balance of your organization |
| `codcel login` | Sign in with an email link, or save an API token |
| `codcel logout` | Remove saved credentials |
| `codcel auth status` | Show which credentials are in use, and for which user and organization |
| `codcel init` | Write a `codcel.toml` project file with every option documented |
| `codcel completions <shell>` | Print a shell completion script (`bash`, `zsh`, `fish`, `powershell`, `elvish`) |

Run `codcel help <command>` for the full list of options of any command. Global options, accepted
by every command:

| Option | Description |
|--------|-------------|
| `-q`, `--quiet` | Only print warnings and errors |
| `-v`, `--verbose` | Print more detail. `-vv` adds the transpiler's log output |
| `--color <auto\|always\|never>` | When to use colors. `NO_COLOR` is honoured |

---

## Authentication and Licensing

Code generated **without** credentials is free and carries a *Non-Commercial* license notice.
To generate commercially licensed code, the CLI needs credentials for your Codcel organization;
each run then spends credits, exactly as the desktop app does.

The CLI looks for credentials in this order and uses the first it finds:

1. The **`CODCEL_TOKEN`** environment variable — an [API token](./api-tokens.md). Use this in CI/CD.
2. A token file given with **`--token-file`** (or `CODCEL_TOKEN_FILE`) — convenient with Docker
   and Kubernetes secrets.
3. Credentials saved by **`codcel login`** — for your own machine.

There is deliberately no `--token` option: secrets passed as command-line arguments end up in
shell history and are visible to other users in the process list.

### Signing in on your machine

```bash
codcel login
```

Codcel emails you a sign-in link, the same as the desktop app. Open it on any device; the CLI
finishes signing in by itself. If your account belongs to several organizations you choose one,
and can switch per run with `--org <name or id>`.

Credentials are stored in the macOS Keychain or Windows Credential Manager. On Linux they are
stored in `~/.config/codcel/credentials.json`, readable only by you. To save an API token
instead of signing in:

```bash
echo "$MY_TOKEN" | codcel login --with-token
```

`codcel auth status` shows what is in use, and `codcel logout` removes saved credentials.

### API tokens for pipelines

Organization owners create API tokens in their Codcel account under **Account → API tokens**.
A token belongs to one organization, can be given an expiry date, and can be revoked at any time.
See [API Tokens](./api-tokens.md).

```bash
export CODCEL_TOKEN=codcel_pat_…      # from a CI secret, never committed
codcel generate model.xlsx --targets java --require-auth
```

!!! warning "Use `--require-auth` in CI"
    Without credentials the CLI still succeeds and produces Non-Commercial code. In a pipeline,
    `--require-auth` (or `CODCEL_REQUIRE_AUTH=true`) turns a missing or misnamed secret into a
    failed build instead.

### License notices

| Credentials | Organization | Generated code |
|-------------|--------------|----------------|
| none, or `--non-commercial` | — | Non-Commercial license notice, no credits spent |
| API token or login | standard (credits) | Commercial license, credits spent |
| API token or login | unlimited plan | Commercial license, usage recorded, no credits deducted |
| API token or login | evaluation (demo) | Evaluation-only license notice |

---

## Credits

A run costs the sum of the prices of what it generates: the base (Rust calculation library,
model library and tables), plus each selected target. `codcel targets` shows current prices for
your account.

```bash
codcel generate model.xlsx --targets all --dry-run
```

- **`--dry-run`** prints the targets and the cost, then stops. Nothing is written and nothing is spent.
- **`--max-credits <N>`** (or `CODCEL_MAX_CREDITS`) refuses to run if the cost exceeds `N`, a
  useful guard for pipelines.
- The balance is checked **before** generating, so a run that cannot be paid for stops at once
  (exit code 4).
- Credits are spent only after generation **succeeds**. The code is first written to a hidden
  staging directory and moved into place only once the credits are spent. A failed generation is
  never charged, and a run whose charge fails leaves no output behind.
- A run is charged once, even when the CLI has to retry because of network trouble.

Every run is listed under **Account → Credit usage** in your Codcel account, together with the
name of the API token that made it.

---

## Targets

Without `--targets`, the CLI generates the Rust calculation library, the model library and the
table data. Add targets as a comma-separated list, or use `--targets all`:

```bash
codcel generate model.xlsx --targets python,java-server,typescript-client
```

Targets that others depend on are added automatically and listed in the output, for example
`java-server` adds `java` and `jni`. Names are case-insensitive; the identifiers used in the
desktop app's `codcel.toml` are accepted too.

| Group | Target | Generates | Also adds |
|-------|--------|-----------|-----------|
| Rust | `wasm` | WebAssembly build of the calculation library | |
| Rust | `fullstack-ui` | Dioxus fullstack web UI | `wasm` |
| Rust | `rust-server` | REST server (Axum) | |
| Rust | `rust-client` | Rust web client | |
| Rust | `openapi` | OpenAPI document | |
| Rust | `command-line` | Command-line app for the model | |
| Rust | `mcp-server` | MCP server | |
| JVM | `jni` | JNI bridge | |
| JVM | `java` | Java calculation library | `jni` |
| JVM | `kotlin` | Kotlin calculation library | `jni` |
| JVM | `java-server` | Java REST server | `java`, `jni` |
| JVM | `kotlin-server` | Kotlin REST server | `kotlin`, `jni` |
| JVM | `java-client` | Java web client | |
| JVM | `kotlin-client` | Kotlin web client | |
| Native | `ffi` | C FFI library | |
| .NET | `csharp` | C# calculation library | `ffi` |
| .NET | `visual-basic` | Visual Basic calculation library | `ffi` |
| .NET | `csharp-server` | C# REST server | `csharp`, `ffi` |
| .NET | `csharp-client` | C# web client | |
| Python | `python` | Python calculation library | `ffi` |
| Python | `python-client` | Python web client | |
| Python | `xlwings` | Excel Python interface (xlwings) | `python`, `ffi` |
| Python | `xlwings-client` | Excel web client Python interface (xlwings) | `python-client` |
| Go | `go` | Go calculation library | `ffi` |
| Go | `go-server` | Go REST server | `go`, `ffi` |
| Go | `go-client` | Go web client | |
| Web | `javascript-client` | JavaScript web client | |
| Web | `typescript-client` | TypeScript web client | |
| Swift | `swift` | Swift calculation library | `ffi` |

See [Output Targets](./output-targets.md) for what each target contains.

---

## Output

| Option | Default | Description |
|--------|---------|-------------|
| `-o`, `--output <DIR>` | `./codcel-output` | Directory the project is written into. `--generated` / `-g` is an alias |
| `-p`, `--project <NAME>` | workbook file name | Project name, used for directory and package names. Spaces become `-`; otherwise use letters, digits, `-` and `_`, starting with a letter |
| `--table-path <DIR>` | `<output>/tables` | Directory for the generated table data |
| `--table-type <TYPE>` | `parquet` | Table storage backend for the generated code: `parquet`, `csv` or `crud` |
| `--clean` | off | Delete the project's existing output directory first |

Without `--clean`, regenerating overwrites the generated files but keeps anything else in the
project directory, such as build output (`target/`, `node_modules/`) and your own notes.

---

## Project Files

A project file keeps a project's options under version control instead of in a long command
line. It is the same `codcel.toml` the desktop app writes, so a desktop project can be generated
in CI unchanged:

```bash
codcel generate --config my-project/codcel.toml
```

Running `codcel generate` with no workbook inside a directory that contains a `codcel.toml`
uses that file automatically.

`codcel init` writes a new project file with every option and a comment explaining it:

```bash
codcel init my-project --excel-path model.xlsx
```

**Precedence:** an option given on the command line overrides the project file, which overrides
the defaults. Relative paths in the file are resolved against the file's directory.

| Section | Contents |
|---------|----------|
| `[project]` | `name` |
| `[files]` | The workbook, e.g. `"model.xlsx" = "business_specs/model.xlsx"` |
| `[formatting]` | Formatting and calculation settings, as on the desktop app's Settings page (see the table [below](#relationship-to-codceltoml)) |
| `[settings]` | The desktop app's target checkboxes (`use_codcel_python_calculation_library = true`, …) |
| `[cli]` | CLI-only options; the desktop app ignores this section |

The `[cli]` section accepts `output`, `table_path`, `table_type`, `targets` (a list such as
`["python", "java-server"]` or `["all"]`; when present it replaces `[settings]`), `language`,
`large_array_threshold`, `csv_files`, `parquet_files`, `discover_data`, `io_config` and the four
`*_engine_version` keys.

When the file comes from the desktop app, output defaults to the project's `code/` and `tables/`
directories, data files next to the workbook are picked up automatically, and the project's
`codcel-io.toml` is applied — the same as generating in the desktop app.

---

## Generation Options

### Formatting

| Option | Short | Default | Description |
|--------|-------|---------|-------------|
| `--locale <TAG>` | | | Locale tag such as `de-DE`. Fills in the four settings below in one go |
| `--decimal-separator <CHAR>` | `-d` | `.` | Decimal separator character |
| `--currency-symbol <SYMBOL>` | `-c` | `$` | Currency symbol. Where it sits relative to the amount comes from the locale, not from here |
| `--thousands-separator <CHAR>` | `-t` | `,` | Thousands separator character |
| `--language <CODE>` | | `en` | Formatting language code |
| `--timezone <ZONE>` | | | IANA timezone for `NOW` and `TODAY`, e.g. `Europe/Berlin`. Empty means the host's local zone at run time |

`--locale` is the quickest way to get a consistent set:

```bash
codcel generate model.xlsx --locale de-DE
```

That yields `,` decimal, `.` thousands, `€`, language `de` and region `DE`. The four individual
options still override it **where they were given a non-default value**, so
`--locale de-DE --currency-symbol CHF` is German conventions with a Swiss franc.

The corollary is that an individual option cannot force a value that happens to equal its own
default: `--locale de-DE --decimal-separator .` still yields `,`, because an option left at its
default is indistinguishable from one that was never passed. Use `--locale en` and set the others
explicitly if that is what you want.

`--timezone` is deliberately **not** derived from `--locale`. A locale is not a timezone: the
United States spans six zones under `en-US`, and Spain and the Canaries share `es-ES` an hour apart.

### Calculation

| Option | Short | Default | Description |
|--------|-------|---------|-------------|
| `--use-excel-rounding[=BOOL]` | `-u` | `true` | Round results to Excel's 15-digit precision |
| `--strict-type-conversion[=BOOL]` | `-s` | `true` | Strict type conversion |
| `--enable-iterative-calculation[=BOOL]` | | `false` | Resolve circular references by iteration |
| `--maximum-iterations <N>` | | `100` | Maximum iterations for convergence |
| `--maximum-change <X>` | | `0.001` | Convergence threshold |

On/off options accept a bare form and an explicit value: `--use-excel-rounding` means `true`,
and `--use-excel-rounding=false` turns it off. The value must follow an `=`.

!!! note "Defaults match the desktop app"
    `--use-excel-rounding` and `--strict-type-conversion` default to `true`, as in the desktop
    app. The CLI's number formatting defaults (`.`, `,`, `$`) differ from the desktop app's
    (`,`, `.`, `€`); set `--locale` or use a project file to get identical output from both.

### Data Files

| Option | Default | Description |
|--------|---------|-------------|
| `--csv-files <FILE>…` | | CSV files with table data |
| `--csv-has-header[=BOOL]` | `false` | The CSV files have a header row |
| `--csv-delimiter <CHAR>` | `;` | CSV field delimiter |
| `--parquet-files <FILE>…` | | Parquet files with table data |
| `--discover-data` | off | Use every `.csv` and `.parquet` file next to the workbook, as the desktop app does |

List several files after one option, or repeat the option — but don't separate them with
commas:

```bash
codcel generate model.xlsx --csv-files T_Measurements.csv T_Stations.csv --csv-has-header
codcel generate model.xlsx --parquet-files Sales.parquet --parquet-files Sales_part1.parquet
```

Parquet files are self-describing, so no header or delimiter settings are needed. Multiple
Parquet files can provide data for the same table using prefix naming (e.g. `Sales.parquet`,
`Sales_part1.parquet`). If both Parquet and CSV files exist for the same table, the Parquet files
take priority.

### Date Handling

| Option | Default | Description |
|--------|---------|-------------|
| `--allow-lotus-1-2-3-1900-date-bug[=BOOL]` | follows the workbook setting | Replicate Excel's 1900 leap year bug in the *generated project* |
| `--workbook-lotus-1-2-3-1900-date-bug[=BOOL]` | `true` | Replicate the bug when *decoding* serials read out of the workbook |
| `--date-system <SYSTEM>` | `auto` | Serial epoch of the source workbook: `auto`, `1900` or `1904` |

Leave `--workbook-lotus-1-2-3-1900-date-bug` enabled: it is the only convention that agrees with
Excel about which day a stored serial denotes. Setting the two options to different values emits
warning `T29` — see [Date Handling](./differences/date-handling.md) for what that costs.

### Advanced

| Option | Default | Description |
|--------|---------|-------------|
| `--large-array-threshold <N>` | `100` | Row count above which array constants are externalised to separate files (prevents slow compilation) |
| `--generate-cell-outputs[=BOOL]` | `false` | Give each cell of a combined output (`*O*B1:B100*Name` or `*O*A1;C5*Name`) its own Rust function and tests. Off, the cells are calculated and tested only as part of the combined output. Other languages always get just the combined output |
| `--concurrent-combined-outputs[=BOOL]` | `false` | Calculate the values of a combined output concurrently (`tokio::join!`) instead of one after another. This can be faster when the values wait on database tables such as PostgreSQL. Otherwise it is no faster, and repeated lookups are not shared through the cache. A combined output with thousands of values may not compile in this mode. Rust only |

### Inputs & Outputs

Codcel generates inputs and outputs from the `*I*` and `*O*` annotations in your workbook.
`codcel detect-io` adds a review step on top of that: it lists what the generated code will
expose, suggests inputs and outputs from unmarked cells, and saves your choices to a
`codcel-io.toml` file next to the workbook.

```bash
codcel detect-io model.xlsx                 # write codcel-io.toml, then edit it
codcel detect-io model.xlsx --interactive   # choose, label and set field options in the terminal
codcel generate model.xlsx                  # applies codcel-io.toml automatically
```

| `generate` option | Description |
|-------------------|-------------|
| `--io-config <FILE>` | Apply this file. Default: `codcel-io.toml` next to the workbook (or in the desktop project), if it exists |
| `--no-io-config` | Ignore any `codcel-io.toml` |

See [Inputs & Outputs](./inputs-outputs.md) for the file format and the full workflow.

### Engine Versions

Generated projects resolve the four Codcel engines from **crates.io**, pinned to an exact version
so a generated calculation keeps producing identical numbers — `cargo update` cannot move an
engine underneath it:

```toml
codcel-calculation-engine = { version = "=0.1.10" }
```

When you are signed in, the CLI asks Codcel which engine versions this CLI release is certified
with, the same way the desktop app does. Otherwise it uses the versions built into the CLI. To
choose versions yourself:

| Option | Description |
|--------|-------------|
| `--calculation-engine-version <REQ>` | crates.io version requirement for codcel-calculation-engine (e.g. `=0.1.9`, `0.1`, `^0.2`) |
| `--table-engine-version <REQ>` | crates.io version requirement for codcel-table-engine |
| `--parquet-engine-version <REQ>` | crates.io version requirement for codcel-parquet-engine |
| `--postgresql-engine-version <REQ>` | crates.io version requirement for codcel-postgresql-engine |

The version string is passed through verbatim, so any Cargo requirement syntax works.

---

## Scripting

### Exit codes

| Code | Meaning |
|------|---------|
| `0` | Success |
| `1` | Generation failed (the workbook could not be loaded or transpiled) |
| `2` | Invalid command-line usage |
| `3` | Authentication failed: missing (with `--require-auth`), invalid, expired or revoked credentials |
| `4` | Not enough credits, or the cost exceeds `--max-credits` |
| `5` | The Codcel API could not be reached, or this CLI version is no longer supported |
| `6` | The transpiler reported errors — or warnings, with `--fail-on-warnings` |

With exit code 6 the output has been generated (and paid for); the errors point at cells whose
generated code will not compile or will not match Excel. Messages link to
[Error Codes](./error-codes.md).

### JSON output

`--output-format json` (or `CODCEL_OUTPUT_FORMAT=json`) prints a single JSON document on
standard output when the command finishes; progress and messages go to standard error.

```bash
codcel generate model.xlsx --targets python --output-format json > result.json
```

```json
{
  "ok": true,
  "dry_run": false,
  "version": "0.2.0",
  "workbook": "/work/model.xlsx",
  "project": "model",
  "output_dir": "/work/codcel-output",
  "project_dir": "/work/codcel-output/model",
  "table_path": "/work/codcel-output/tables",
  "targets": ["ffi", "python"],
  "added_as_required": ["ffi"],
  "license": "commercial",
  "billing": {
    "organization": { "id": "…", "name": "Acme", "kind": "standard" },
    "user": "ci@acme.example",
    "cost": 85,
    "credits_spent": 85,
    "balance_before": 1200,
    "balance_after": 1115,
    "request_id": "…"
  },
  "compiler": { "errors": 0, "warnings": 1, "messages": [ { "level": "warning", "code": "WCK5", "message": "…", "sheet": null, "cell": null } ] },
  "duration_secs": 4.21
}
```

`codcel targets`, `codcel credits` and `codcel auth status` accept `--output-format json` too.

### Environment variables

| Variable | Equivalent option | Description |
|----------|-------------------|-------------|
| `CODCEL_TOKEN` | — | API token. Takes precedence over all other credentials |
| `CODCEL_TOKEN_FILE` | `--token-file` | File containing the API token |
| `CODCEL_ORG` | `--org` | Organization to use with a login that belongs to several |
| `CODCEL_REQUIRE_AUTH` | `--require-auth` | `true` to fail when no credentials are found |
| `CODCEL_MAX_CREDITS` | `--max-credits` | Spending limit per run |
| `CODCEL_TARGETS` | `--targets` | Comma-separated targets |
| `CODCEL_CONFIG` | `--config` | Project file |
| `CODCEL_OUTPUT_FORMAT` | `--output-format` | `text` or `json` |
| `CODCEL_CONFIG_DIR` | — | Directory for saved credentials, instead of the OS default |
| `NO_COLOR` | `--color never` | Disable colors |
| `HTTPS_PROXY` | — | Proxy for requests to the Codcel API |
| `RUST_LOG` | — | Log filter for the transpiler's diagnostic output, e.g. `info` |

Generation settings such as separators and rounding are deliberately **not** read from the
environment: variables like `CODCEL_DECIMAL_SEPARATOR` configure the *generated* code at run time
(see [Runtime Formatting](./runtime-formatting.md)), and must not silently change what the CLI
generates.

### Shell completions

```bash
codcel completions bash > ~/.local/share/bash-completion/completions/codcel
codcel completions zsh  > "${fpath[1]}/_codcel"
codcel completions fish > ~/.config/fish/completions/codcel.fish
codcel completions powershell >> $PROFILE
```

### Earlier command syntax

Earlier versions of the CLI had no subcommands. That syntax still works: an invocation that
starts with options such as `-e`, `-p` or `-g` is run as `codcel generate`, generates every
target as before, and keeps its earlier defaults and exit code. New scripts should use
`codcel generate` with `--targets`.

---

## Examples

### European number formatting

```bash
codcel generate ./specs/report.xlsx -p quarterly-report --locale de-DE
```

### With CSV data files

```bash
codcel generate ./specs/analysis.xlsx -p data-analysis \
  --csv-files T_Measurements.csv T_Stations.csv --csv-has-header --csv-delimiter ","
```

### Pinning engine versions

```bash
codcel generate ./specs/mortgage.xlsx \
  --calculation-engine-version "=0.1.8" --table-engine-version "=0.1.8" \
  --parquet-engine-version "=0.1.8" --postgresql-engine-version "=0.1.8"
```

### With circular references

```bash
codcel generate ./specs/financial-model.xlsx \
  --enable-iterative-calculation --maximum-iterations 200 --maximum-change 0.0001
```

### Everything, into a clean directory

```bash
codcel generate model.xlsx --targets all -o build/generated --clean
```

---

## Relationship to codcel.toml

The `[formatting]` settings of a project file correspond to these options:

| CLI option | codcel.toml setting |
|------------|---------------------|
| `--locale` | `formatting.locale` |
| `--timezone` | `formatting.timezone` |
| `--decimal-separator` | `formatting.decimal_separator` |
| `--currency-symbol` | `formatting.currency_symbol` |
| `--thousands-separator` | `formatting.thousands_separator` |
| `--strict-type-conversion` | `formatting.strict_type_conversion` |
| `--csv-has-header` | `formatting.csv_has_header` |
| `--csv-delimiter` | `formatting.csv_delimiter` |
| `--use-excel-rounding` | `formatting.use_excel_rounding` |
| `--allow-lotus-1-2-3-1900-date-bug` | `formatting.allow_lotus_1_2_3_1900_date_bug` |
| `--workbook-lotus-1-2-3-1900-date-bug` | `formatting.workbook_lotus_1_2_3_1900_date_bug` |
| `--date-system` | `formatting.date_system` |
| `--enable-iterative-calculation` | `formatting.allow_circular_references` |
| `--maximum-iterations` | `formatting.circular_max_iterations` |
| `--maximum-change` | `formatting.circular_convergence_threshold` |
| `--generate-cell-outputs` | `formatting.generate_cell_outputs` |
| `--concurrent-combined-outputs` | `formatting.concurrent_combined_outputs` |
| `--targets` | `cli.targets`, or the `settings.use_codcel_…` checkboxes |
| `--output`, `--table-path`, `--table-type` | `cli.output`, `cli.table_path`, `cli.table_type` |

Input and output selections are the exception: they are stored in a separate `codcel-io.toml`
file rather than in `codcel.toml`. See [Inputs & Outputs](./inputs-outputs.md).

---

## See Also

- [CI/CD Pipelines](./ci-cd.md) — running the CLI in GitHub Actions, GitLab CI, Azure DevOps, Jenkins and Bitbucket
- [API Tokens](./api-tokens.md) — creating, rotating and revoking tokens
- [Inputs & Outputs](./inputs-outputs.md) — reviewing, renaming and auto-detecting inputs and outputs
- [Settings Reference](./settings.md) — full reference for all configuration options
- [Runtime Formatting](./runtime-formatting.md) — runtime locale detection and `CODCEL_*` environment variable overrides
- [Desktop Application Guide](./desktop-app.md) — using the graphical interface instead
