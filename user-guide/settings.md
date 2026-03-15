<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Settings Reference

Codcel uses two levels of configuration: **global settings** that apply across the application, and **project settings** that are specific to each project.

---

## Global Settings

Global settings are stored in `~/codcel.toml` (in your home directory) and apply to the Codcel application as a whole.

| Setting | Description |
|---------|-------------|
| `projects_location` | Default directory for creating and opening projects |
| `has_seen_onboarding` | Whether you have completed the onboarding wizard |
| `language` | UI language code (e.g. `en`, `fr`, `de`) |

These settings are managed automatically by the application. The projects location is set during onboarding and can be updated from the Home page. The language can be changed from the application interface.

---

## Project Formatting Settings

Each project has its own formatting settings, stored in the `[formatting]` section of the project's `codcel.toml` file. These settings control how Codcel interprets numbers, dates, and other data types when generating code.

To access these settings, open a project and click **Settings** in the sidebar.

### Decimal Separator

**Default:** `,`

The character used as the decimal point in numbers. Set this to match the locale of your Excel file.

- Use `,` for European formats (e.g. `1.234,56`)
- Use `.` for US/UK formats (e.g. `1,234.56`)

### Currency Symbol

**Default:** `€`

The symbol used for currency formatting in the generated code. Common values include `€`, `$`, `£`, and `¥`.

### Thousands Separator

**Default:** `.`

The character used to group digits in large numbers.

- Use `.` for European formats (e.g. `1.234.567`)
- Use `,` for US/UK formats (e.g. `1,234,567`)

### Strict Type Conversion

**Default:** `true` (enabled)

Controls how Codcel handles implicit type conversions between text, numbers, and booleans.

- **Enabled** -- type conversions follow strict rules. Attempting to use a text value where a number is expected will produce an error.
- **Disabled** -- type conversions are more permissive, similar to how Excel silently converts between types.

For more details on type conversion behaviour, see [Type Conversions](./differences/type-conversions.md).

### CSV Has Header

**Default:** `false` (disabled)

Determines whether CSV files imported as tables are treated as having a header row.

- **Enabled** -- the first row of the CSV is treated as column headers
- **Disabled** -- all rows are treated as data

### CSV Delimiter

**Default:** `,`

The character used to separate fields in CSV files. Common values include `,` (comma), `;` (semicolon), and `\t` (tab).

### Use Excel Rounding

**Default:** `true` (enabled)

When enabled, the generated code uses Excel-compatible rounding rules, limiting precision to 15 significant digits. This ensures that calculations match Excel's results exactly.

When disabled, the generated code uses full double-precision floating-point arithmetic, which may produce slightly different results from Excel for very large or very precise numbers.

For more details, see [Rounding Differences](./differences/rounding.md).

### Allow Lotus 1-2-3 1900 Date Bug

**Default:** `true` (enabled)

Excel inherited a date-numbering bug from Lotus 1-2-3 that treats 1900 as a leap year (it was not). When enabled, Codcel replicates this behaviour to ensure date serial numbers match Excel exactly.

Disable this only if your spreadsheet does not use date serial numbers or if you need astronomically correct dates prior to 1 March 1900.

### Enable Iterative Calculation

**Default:** `false` (disabled)

When enabled, Codcel can resolve circular references in your spreadsheet by iterating until convergence. Two additional settings become available:

#### Maximum Iterations

**Default:** `100`

The maximum number of iterations Codcel will perform when resolving circular references. If convergence is not reached within this limit, Codcel stops and uses the last computed values.

#### Maximum Change (Convergence Threshold)

**Default:** `0.001`

The convergence threshold for iterative calculation. Codcel stops iterating when the change between successive iterations for all cells is smaller than this value.

---

## Generation Settings

Generation settings control which output targets Codcel produces when you generate a project. These are managed from the **Generate Project** view in the sidebar and stored in the `[settings]` section of `codcel.toml`.

### Core

| Output Target | Description | Always Available |
|---------------|-------------|:---:|
| Rust Calculation Library | The core calculation engine in Rust -- always generated | Yes |
| Rust Model Library | Data model definitions for the generated Rust code | Yes |
| Tables | Table engine for structured data access | Yes |

The Rust Calculation Library cannot be disabled. It is the foundation upon which all other output targets are built.

### Calculation Libraries

| Output Target | Description |
|---------------|-------------|
| WASM Calculation Library | WebAssembly version of the calculation engine for browser use |
| Java Calculation Library | Java library wrapping the calculation engine via JNI |
| Kotlin Calculation Library | Kotlin library wrapping the calculation engine via JNI |
| C# Calculation Library | C# library wrapping the calculation engine via FFI |
| Visual Basic Calculation Library | Visual Basic library wrapping the calculation engine via FFI |
| Python Calculation Library | Python library wrapping the calculation engine via FFI |
| Go Calculation Library | Go library wrapping the calculation engine via FFI |
| Swift Calculation Library | Swift library wrapping the calculation engine via FFI |

### Servers

| Output Target | Description |
|---------------|-------------|
| RESTful Server (Rust) | REST API server in Rust exposing your calculations as endpoints |
| Java RESTful Server | REST API server in Java |
| Kotlin RESTful Server | REST API server in Kotlin |
| C# Server | REST API server in C# |
| Go RESTful Server | REST API server in Go |

### Web Clients

| Output Target | Description |
|---------------|-------------|
| Rust Web Client | Web client library in Rust for calling the REST API |
| Java Web Client | Web client library in Java |
| Kotlin Web Client | Web client library in Kotlin |
| C# Web Client | Web client library in C# |
| Python Web Client | Web client library in Python |
| Go Web Client | Web client library in Go |
| JavaScript Web Client | Web client library in JavaScript |
| TypeScript Web Client | Web client library in TypeScript |
| Swift Calculation Library | Swift client library |

### Full-Stack and UI

| Output Target | Description |
|---------------|-------------|
| Fullstack UI | A complete web application with server and UI components |

### APIs and Integration

| Output Target | Description |
|---------------|-------------|
| OpenAPI Document | An OpenAPI (Swagger) specification for the generated REST API |
| Command Line | A command-line tool for running calculations from the terminal |
| MCP Server | A Model Context Protocol server for AI integration |
| JNI | Java Native Interface bindings for the Rust calculation engine |
| FFI Library | Foreign Function Interface library for C-compatible bindings |

---

## The `codcel.toml` File

Every Codcel project has a `codcel.toml` file at its root. This file is managed by the desktop application and contains all project configuration. While you can edit it manually, it is recommended to use the application interface.

### Structure

```toml
# Project identity
[project]
name = "my-project"

# Imported spreadsheet files
[files]
spreadsheet.xlsx = "business_specs/spreadsheet.xlsx"

# Formatting and calculation settings
[formatting]
decimal_separator = ","
currency_symbol = "€"
thousands_separator = "."
strict_type_conversion = true
csv_has_header = false
csv_delimiter = ","
use_excel_rounding = true
allow_lotus_1_2_3_1900_date_bug = true
allow_circular_references = false
circular_max_iterations = 100
circular_convergence_threshold = 0.001

# Generation output targets
[settings]
use_codcel_rust_calculation_library = true
use_codcel_wasm_calculation_library = false
use_codcel_fullstack_ui = false
use_codcel_restful_server = false
use_codcel_web_client = false
use_codcel_open_api_document = false
use_codcel_command_line = false
use_codcel_mcp_server = false
use_codcel_jni = false
use_codcel_java_calculation_library = false
use_codcel_kotlin_calculation_library = false
use_codcel_java_restful_server = false
use_kotlin_restful_server = false
use_java_web_client = false
use_kotlin_web_client = false
use_codcel_ffi_library = false
use_codcel_csharp_calculation_library = false
use_codcel_visual_basic_calculation_library = false
use_codcel_csharp_server = false
use_codcel_csharp_webclient = false
use_codcel_python_calculation_library = false
use_python_web_client = false
use_codcel_go_calculation_library = false
use_codcel_go_restful_server = false
use_codcel_go_web_client = false
use_codcel_javascript_web_client = false
use_codcel_typescript_web_client = false
use_codcel_swift_calculation_library = false
```

Changes made through the Settings view and Generate Project view are written to this file automatically when you click Save or Generate.

---

## Runtime Formatting

The settings above control the **default** formatting baked into the generated code at build time. At runtime, the generated code can also detect and apply locale-appropriate formatting automatically using OS locale detection, `CODCEL_*` environment variables, and per-call language overrides.

For full details, see [Runtime Formatting](./runtime-formatting.md).