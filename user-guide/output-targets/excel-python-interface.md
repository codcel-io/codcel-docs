<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Excel Python Interface

Codcel generates Excel workbooks (`.xlsm`) with [xlwings](https://www.xlwings.org/) integration, providing a familiar spreadsheet interface for your Python-powered calculations. Users interact with Excel as usual while xlwings calls the generated Python calculation library behind the scenes.

---

## What It Generates

For each calculation method in your Excel model, Codcel generates:

- An `.xlsm` workbook with embedded VBA macros for xlwings integration
- A custom ribbon tab for triggering calculations directly from Excel
- Pre-configured cell layouts matching your model's inputs and outputs
- A `requirements.txt` for Python dependencies
- A `README.md` with setup and usage instructions

The output directory is `<project-name>-excel-python-xlwings/`, with a subdirectory per calculation method:

```
<project-name>-excel-python-xlwings/
    requirements.txt
    README.md
    monthly_payment/
        monthly_payment.xlsm
    amortization_schedule/
        amortization_schedule.xlsm
```

---

## Platform Support

xlwings requires Microsoft Excel for its Python-Excel communication layer.

| Platform | Supported | Application |
|----------|:---------:|-------------|
| Windows  | Yes       | Microsoft Excel (required) |
| macOS    | Yes       | Microsoft Excel (required) |
| Linux    | No        | xlwings does not support Linux |

!!! warning "Linux"
    xlwings requires Microsoft Excel, which is not available on Linux. The generated `.xlsm` files can be opened in LibreOffice Calc, but the xlwings Python integration will not function.

---

## Prerequisites

- **Python 3.8+** with xlwings installed:

    ```bash
    pip install xlwings
    ```

- **Microsoft Excel** (Windows or macOS)

- The **FFI Library** and **Python Calculation Library** must be built first (see [Build Order](#build-order) below)

---

## How It Works

1. The user opens a generated `.xlsm` workbook in Microsoft Excel
2. Input values are entered into the designated input cells
3. The user clicks a button on the custom ribbon tab (or runs a VBA macro)
4. xlwings passes the input values from Excel to the Python calculation library
5. The Python library calls the Rust FFI engine to perform the calculation
6. Results are written back into the output cells in Excel

```
Excel (.xlsm)  <-->  xlwings (VBA + Python)  <-->  Python Calc Library  <-->  Rust FFI Engine
```

---

## Dependencies

The Excel Python Interface depends on:

| Dependency | Purpose |
|-----------|---------|
| Rust Calculation Library | Core calculation engine |
| FFI Library | C-compatible bridge for Python |
| Python Calculation Library | Python wrapper around the FFI engine |

When selecting the Excel Python Interface in the desktop app, the Python Calculation Library and FFI Library are automatically selected.

---

## Build Order

1. Build the Rust Calculation Library: `cargo build --release` in the calculation directory
2. Build the FFI Library: `cargo build --release` in the `ffi/` directory
3. Install the Python Calculation Library: `pip install .` in the Python calculation directory
4. Install xlwings dependencies: `pip install -r requirements.txt` in the `excel-python-xlwings/` directory
5. Open the `.xlsm` file in Microsoft Excel

---

## Setup

After generating the project:

```bash
# 1. Build the Rust calculation engine
cd <project-name>-calculation
cargo build --release

# 2. Build the FFI library
cd ../<project-name>-ffi
cargo build --release

# 3. Install the Python calculation library
cd ../<project-name>-calculation-python
pip install .

# 4. Install xlwings and other dependencies
cd ../<project-name>-excel-python-xlwings
pip install -r requirements.txt

# 5. Open a workbook in Excel
open monthly_payment/monthly_payment.xlsm   # macOS
start monthly_payment/monthly_payment.xlsm  # Windows
```

---

## UI Configuration from Excel

You can customise the generated Excel workbooks by adding a `codcel-ui-layouts` configuration sheet to your Excel workbook:

- **`codcel-ui-layouts`** -- control field ordering and visual grouping

When a `codcel-ui-layouts` sheet is present, inputs and outputs are reordered according to the layout, and `group` entries are rendered as styled header rows in the generated workbook, making it easy to organise complex models with many inputs and outputs.

For full details, see [UI Configuration](../ui-configuration.md).

---

## Selecting in the Desktop App

In the **Generate Project** view, the Excel Python Interface checkbox appears under the **Excel** separator in the Python section. Selecting it automatically enables:

- Codcel Python Calculation Library
- Codcel FFI Library

These dependencies cannot be deselected while the Excel Python Interface is selected.
