<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Command Line Interface

Codcel can be run from the command line for automated workflows, CI/CD pipelines, and scripted code generation. The CLI accepts the same configuration options available in the desktop app.

---

## Basic Usage

```bash
codcel -e spreadsheet.xlsx -p my-project -g ./generated --table-path ./tables
```

---

## Arguments

### Required

| Argument | Short | Description |
|----------|-------|-------------|
| `--excel-path` | `-e` | Path to the Excel file to transpile |
| `--project` | `-p` | Project name (used in generated code identifiers) |
| `--generated` | `-g` | Output directory for generated project files |
| `--table-path` | | Path where generated table files are stored |

### Table Format

| Argument | Default | Description |
|----------|---------|-------------|
| `--table-type` | | Format for generated tables: `csv` or `parquet` |

### Formatting

| Argument | Short | Default | Description |
|----------|-------|---------|-------------|
| `--locale` | | | Locale tag such as `de-DE`. Fills in the four settings below in one go |
| `--decimal-separator` | `-d` | `.` | Decimal separator character |
| `--currency-symbol` | `-c` | `$` | Currency symbol. Where it sits relative to the amount comes from the locale, not from here |
| `--thousands-separator` | `-t` | `,` | Thousands separator character |
| `--language` | | `en` | Formatting language code |
| `--timezone` | | | IANA timezone for `NOW` and `TODAY`, e.g. `Europe/Berlin`. Empty means the host's local zone at run time |

`--locale` is the quickest way to get a consistent set:

```bash
codcel -e model.xlsx -p my-project --locale de-DE
```

That yields `,` decimal, `.` thousands, `€`, language `de` and region `DE`. The
four individual flags still override it **where they were given a non-default
value**, so `--locale de-DE --currency-symbol CHF` is German conventions with a
Swiss franc.

The corollary is that an individual flag cannot force a value that happens to
equal its own default: `--locale de-DE --decimal-separator .` still yields `,`,
because a flag left at its default is indistinguishable from one that was never
passed. Use `--locale en` and set the others explicitly if that is what you want.

`--timezone` is deliberately **not** derived from `--locale`. A locale is not a
timezone: the United States spans six zones under `en-US`, and Spain and the
Canaries share `es-ES` an hour apart.

### Type Handling

| Argument | Short | Default | Description |
|----------|-------|---------|-------------|
| `--strict-type-conversion` | `-s` | `false` | Enable strict type conversion |
| `--use-excel-rounding` | `-u` | `false` | Use Excel's 15-digit rounding |

### CSV Configuration

| Argument | Default | Description |
|----------|---------|-------------|
| `--csv-files` | *(empty)* | Comma-separated list of CSV file paths |
| `--csv-has-header` | `false` | Whether CSV files have a header row |
| `--csv-delimiter` | `;` | CSV field delimiter character |

### Parquet Input Configuration

| Argument | Default | Description |
|----------|---------|-------------|
| `--parquet-files` | *(empty)* | Comma-separated list of Parquet file paths for table data input |

Parquet files are self-describing, so no header or delimiter settings are needed. Multiple Parquet files can provide data for the same table using prefix naming (e.g., `Sales.parquet`, `Sales_part1.parquet`). If both Parquet and CSV files exist for the same table, the Parquet files take priority.

### Date Handling

| Argument | Default | Description |
|----------|---------|-------------|
| `--allow-lotus-1-2-3-1900-date-bug` | follows the workbook setting | Replicate Excel's 1900 leap year bug in the *generated project* |
| `--workbook-lotus-1-2-3-1900-date-bug` | `true` | Replicate the bug when *decoding* serials read out of the workbook |
| `--date-system` | `auto` | Serial epoch of the source workbook: `auto`, `1900` or `1904` |

Both bug flags accept a bare form and an explicit value, so either of these works:

```bash
--allow-lotus-1-2-3-1900-date-bug          # same as =true
--allow-lotus-1-2-3-1900-date-bug=false
```

Leave `--workbook-lotus-1-2-3-1900-date-bug` enabled: it is the only convention that agrees with Excel about which day a stored serial denotes. Setting the two flags to different values emits warning `T29` — see [Date Handling](./differences/date-handling.md) for what that costs.

### Iterative Calculation

| Argument | Default | Description |
|----------|---------|-------------|
| `--enable-iterative-calculation` | `false` | Enable circular reference resolution |
| `--maximum-iterations` | `100` | Maximum iterations for convergence |
| `--maximum-change` | `0.001` | Convergence threshold |

### Advanced

| Argument | Default | Description |
|----------|---------|-------------|
| `--large-array-threshold` | `100` | Row count above which array constants are externalised to separate files (prevents slow compilation) |
| `--templates` | *(empty)* | Path to the template directory. Only required when Codcel is built without the `embedded-templates` feature |

### Inputs & Outputs

Codcel generates inputs and outputs from the `*I*` and `*O*` annotations in your workbook. These
flags add a review step on top of that: they list what the generated code will expose, let Codcel
suggest inputs and outputs from unmarked cells, and save your choices to a `codcel-io.toml`
sidecar file.

| Argument | Default | Description |
|----------|---------|-------------|
| `--detect-io` | `false` | List the workbook's annotations plus detected candidates, write them to the config file, then exit without transpiling |
| `--detect-io-interactive` | `false` | The same list, reviewed in an interactive terminal checklist, then transpile in the same run |
| `--io-config` | *(empty)* | Path to a `codcel-io.toml` to apply. Also chooses where `--detect-io` writes. Defaults to `codcel-io.toml` next to the Excel file |

Passing none of these flags means no config file is read or written, so existing scripts behave
exactly as before. See [Inputs & Outputs](./inputs-outputs.md) for the file format and the full
workflow.

### Engine Versions

Generated projects resolve the four Codcel engines from **crates.io**. You do not need to pass anything: with no flags, the generated `Cargo.toml` pins the version of each engine that ships with your transpiler, as an exact requirement:

```toml
codcel-calculation-engine = { version = "=0.1.9" }
```

The pin is exact by design. A generated calculation must keep producing identical numbers, so `cargo update` must not be able to move an engine underneath it. To upgrade, regenerate the project with a newer transpiler, or pass an explicit version.

| Argument | Default | Description |
|----------|---------|-------------|
| `--calculation-engine-version` | *(built-in)* | crates.io version requirement for codcel-calculation-engine (e.g. `=0.1.9`, `0.1`, `^0.2`) |
| `--table-engine-version` | *(built-in)* | crates.io version requirement for codcel-table-engine |
| `--parquet-engine-version` | *(built-in)* | crates.io version requirement for codcel-parquet-engine |
| `--postgresql-engine-version` | *(built-in)* | crates.io version requirement for codcel-postgresql-engine |

The version string is passed through verbatim, so any Cargo requirement syntax works.

#### Git overrides

For development and PR testing you can point an engine at a git **tag** or **branch** instead. These are an escape hatch for testing generated code against unreleased engine work — released projects should use crates.io versions.

| Argument | Default | Description |
|----------|---------|-------------|
| `--calculation-engine-tag` | *(empty)* | Git tag for codcel-calculation-engine (e.g. `release-0.1.9`) |
| `--calculation-engine-branch` | *(empty)* | Git branch for codcel-calculation-engine (e.g. `feature/my-branch`) |
| `--table-engine-tag` | *(empty)* | Git tag for codcel-table-engine |
| `--table-engine-branch` | *(empty)* | Git branch for codcel-table-engine |
| `--parquet-engine-tag` | *(empty)* | Git tag for codcel-parquet-engine |
| `--parquet-engine-branch` | *(empty)* | Git branch for codcel-parquet-engine |
| `--postgresql-engine-tag` | *(empty)* | Git tag for codcel-postgresql-engine |
| `--postgresql-engine-branch` | *(empty)* | Git branch for codcel-postgresql-engine |

Each engine resolves independently, using the first of these that is set:

1. `--<engine>-engine-tag` — git dependency at that tag
2. `--<engine>-engine-branch` — git dependency on that branch
3. `--<engine>-engine-version` — crates.io dependency at that version
4. nothing — crates.io dependency at the transpiler's built-in version

---

## Examples

### Basic Generation

```bash
codcel \
  -e ./business_specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
--table-path ./tables
```

### European Number Formatting

```bash
codcel \
  -e ./specs/report.xlsx \
  -p quarterly-report \
  -g ./generated \
--table-path ./tables \
  -d "," \
  -t "." \
  -c "€"
```

### With CSV Data Files

```bash
codcel \
  -e ./specs/analysis.xlsx \
  -p data-analysis \
  -g ./generated \
--table-path ./tables \
  --table-type parquet \
  --csv-files "T_Measurements.csv,T_Stations.csv" \
  --csv-has-header \
  --csv-delimiter ","
```

### With Parquet Data Files

```bash
codcel \
  -e ./specs/analysis.xlsx \
  -p data-analysis \
  -g ./generated \
--table-path ./tables \
  --table-type parquet \
  --parquet-files "T_Measurements.parquet,T_Measurements_part2.parquet"
```

### Pinning a Specific Published Version

```bash
codcel \
  -e ./specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
--table-path ./tables \
  --table-type parquet \
  --calculation-engine-version "=0.1.8" \
  --table-engine-version "=0.1.8" \
  --parquet-engine-version "=0.1.8" \
  --postgresql-engine-version "=0.1.8"
```

### Testing a Feature Branch

Use `--*-engine-branch` to point one engine at a development branch. Engines resolve independently, so here the calculation engine comes from git while the other three stay on crates.io:

```bash
codcel \
  -e ./specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
--table-path ./tables \
  --table-type parquet \
  --calculation-engine-branch feature/new-rounding
```

### Detecting Inputs and Outputs

Write the detected inputs and outputs to a file, review it, then transpile with your selections
applied:

```bash
# Detect and write the file, then exit
codcel \
  -e ./specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
--table-path ./tables \
  --table-type parquet \
  --detect-io \
  --io-config ./codcel-io.toml

# Edit ./codcel-io.toml, then generate with those selections
codcel \
  -e ./specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
--table-path ./tables \
  --table-type parquet \
  --io-config ./codcel-io.toml
```

Use `--detect-io-interactive` instead to review the list in a terminal checklist and transpile in
a single run.

### With Circular References

```bash
codcel \
  -e ./specs/financial-model.xlsx \
  -p financial-model \
  -g ./generated \
--table-path ./tables \
  --enable-iterative-calculation \
  --maximum-iterations 200 \
  --maximum-change 0.0001
```

---

## CI/CD Integration

The CLI is well suited for automated pipelines. A typical CI/CD step:

```yaml
# Example GitHub Actions step
- name: Generate code from Excel
  run: |
    codcel \
      -e ./business_specs/calculations.xlsx \
      -p my-project \
      -g ./generated \
      --table-path ./tables \
      --table-type parquet
```

After generation, use standard build tools to compile and test the generated code:

```yaml
- name: Build and test
  run: |
    cd generated/rust-calculation
    cargo build --release
    cargo test
```

---

## Relationship to codcel.toml

The CLI arguments correspond to settings in `codcel.toml`. The desktop app reads and writes `codcel.toml`, while the CLI accepts the same values as command-line flags.

| CLI Argument | codcel.toml Setting |
|-------------|---------------------|
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

Input and output selections are the exception: they are stored in a separate `codcel-io.toml`
sidecar file rather than in `codcel.toml`. The CLI reads it via `--io-config`, and the desktop
app reads it from the project folder automatically. See
[Inputs & Outputs](./inputs-outputs.md).

---

## See Also

- [Inputs & Outputs](./inputs-outputs.md) -- reviewing, renaming and auto-detecting inputs and outputs
- [Settings Reference](./settings.md) -- full reference for all configuration options
- [Runtime Formatting](./runtime-formatting.md) -- runtime locale detection and `CODCEL_*` environment variable overrides
- [Desktop Application Guide](./desktop-app.md) -- using the graphical interface instead
- [Excel to Code](./excel-to-code.md) -- the complete workflow from spreadsheet to code