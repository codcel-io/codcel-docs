<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Command Line Interface

Codcel can be run from the command line for automated workflows, CI/CD pipelines, and scripted code generation. The CLI accepts the same configuration options available in the desktop app.

---

## Basic Usage

```bash
codcel -e spreadsheet.xlsx -p my-project -g ./generated --templates /path/to/templates --table-path ./tables
```

---

## Arguments

### Required

| Argument | Short | Description |
|----------|-------|-------------|
| `--excel-path` | `-e` | Path to the Excel file to transpile |
| `--project` | `-p` | Project name (used in generated code identifiers) |
| `--generated` | `-g` | Output directory for generated project files |
| `--templates` | | Path to the Codcel templates directory |
| `--table-path` | | Path where generated table files are stored |

### Table Format

| Argument | Default | Description |
|----------|---------|-------------|
| `--table-type` | | Format for generated tables: `csv` or `parquet` |

### Formatting

| Argument | Short | Default | Description |
|----------|-------|---------|-------------|
| `--decimal-separator` | `-d` | `.` | Decimal separator character |
| `--currency-symbol` | `-c` | `$` | Currency symbol |
| `--thousands-separator` | `-t` | `,` | Thousands separator character |
| `--language` | | `en` | Formatting language code |

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

### Date Handling

| Argument | Default | Description |
|----------|---------|-------------|
| `--allow-lotus-1-2-3-1900-date-bug` | `true` | Replicate Excel's 1900 leap year bug |

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

---

## Examples

### Basic Generation

```bash
codcel \
  -e ./business_specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
  --templates /opt/codcel/templates \
  --table-path ./tables
```

### European Number Formatting

```bash
codcel \
  -e ./specs/report.xlsx \
  -p quarterly-report \
  -g ./generated \
  --templates /opt/codcel/templates \
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
  --templates /opt/codcel/templates \
  --table-path ./tables \
  --table-type parquet \
  --csv-files "T_Measurements.csv,T_Stations.csv" \
  --csv-has-header \
  --csv-delimiter ","
```

### With Circular References

```bash
codcel \
  -e ./specs/financial-model.xlsx \
  -p financial-model \
  -g ./generated \
  --templates /opt/codcel/templates \
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
      --templates ${{ env.CODCEL_TEMPLATES }} \
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
| `--decimal-separator` | `formatting.decimal_separator` |
| `--currency-symbol` | `formatting.currency_symbol` |
| `--thousands-separator` | `formatting.thousands_separator` |
| `--strict-type-conversion` | `formatting.strict_type_conversion` |
| `--csv-has-header` | `formatting.csv_has_header` |
| `--csv-delimiter` | `formatting.csv_delimiter` |
| `--use-excel-rounding` | `formatting.use_excel_rounding` |
| `--allow-lotus-1-2-3-1900-date-bug` | `formatting.allow_lotus_1_2_3_1900_date_bug` |
| `--enable-iterative-calculation` | `formatting.allow_circular_references` |
| `--maximum-iterations` | `formatting.circular_max_iterations` |
| `--maximum-change` | `formatting.circular_convergence_threshold` |

---

## See Also

- [Settings Reference](./settings.md) -- full reference for all configuration options
- [Runtime Formatting](./runtime-formatting.md) -- runtime locale detection and `CODCEL_*` environment variable overrides
- [Desktop Application Guide](./desktop-app.md) -- using the graphical interface instead
- [Excel to Code](./excel-to-code.md) -- the complete workflow from spreadsheet to code