<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Excel Web Client Python Interface

Codcel generates Excel workbooks (`.xlsm`) with [xlwings](https://www.xlwings.org/) integration that call a remote REST API via the Python Web Client. Users interact with Excel as usual while xlwings sends input values to a running Codcel server over HTTP and writes the results back into the worksheet.

---

## What It Generates

For each calculation method in your Excel model, Codcel generates:

- An `.xlsm` workbook with embedded VBA macros for xlwings integration
- A Python script that reads inputs from Excel, calls the web API, and writes outputs back
- A custom ribbon tab for triggering calculations directly from Excel
- Pre-configured cell layouts matching your model's inputs and outputs
- A `requirements.txt` for Python dependencies (`xlwings`, `pydantic`, `requests`)
- A `README.md` with setup and usage instructions

The output directory is `<project-name>-excel-web-client-python-xlwings/`, with a subdirectory per calculation method:

```
<project-name>-excel-web-client-python-xlwings/
    requirements.txt
    README.md
    monthly_payment/
        monthly_payment.xlsm
        monthly_payment.py
    amortization_schedule/
        amortization_schedule.xlsm
        amortization_schedule.py
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

- **Python 3.7+** with xlwings installed:

    ```bash
    pip install xlwings
    ```

- **Microsoft Excel** (Windows or macOS)

- A **running Codcel REST server** at `http://localhost:3030` (or your configured host)

- The **Python Web Client** project must be installed (see [Build Order](#build-order) below)

---

## How It Works

1. The user opens a generated `.xlsm` workbook in Microsoft Excel
2. Input values are entered into the designated input cells
3. The user clicks a button on the custom ribbon tab (or runs a VBA macro)
4. xlwings passes the input values from Excel to the Python script
5. The Python script calls the Python Web Client, which sends an HTTP request to the REST server
6. Results are written back into the output cells in Excel

```
Excel (.xlsm)  <-->  xlwings (VBA + Python)  <-->  HTTP Request  <-->  Python Web Client  <-->  REST API Server
```

---

## Dependencies

The Excel Web Client Python Interface depends on:

| Dependency | Purpose |
|-----------|---------|
| Python Web Client | HTTP client library that calls the REST API |
| REST Server | Any Codcel-generated server (Rust, Java, Kotlin, C#, or Go) |

When selecting the Excel Web Client Python Interface in the desktop app, the Python Web Client is automatically selected.

---

## Build Order

1. Build and start a REST server (e.g., `cargo run --release` in the Rust server directory)
2. Install the Python Web Client: `pip install .` in the web client directory
3. Install xlwings dependencies: `pip install -r requirements.txt` in the `excel-web-client-python-xlwings/` directory
4. Open the `.xlsm` file in Microsoft Excel

---

## Setup

After generating the project:

```bash
# 1. Start a REST server (e.g., the Rust server) in a separate terminal
cd <project-name>-server
cargo run --release

# 2. Install the Python Web Client
cd ../<project-name>-web-client-python
pip install .

# 3. Install xlwings and other dependencies
cd ../<project-name>-excel-web-client-python-xlwings
pip install -r requirements.txt

# 4. Open a workbook in Excel
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

In the **Generate Project** view, the Excel Web Client Python Interface checkbox appears under the **Excel** separator in the Python section. Selecting it automatically enables:

- Codcel Python Web Client

The Python Web Client cannot be deselected while the Excel Web Client Python Interface is selected.
