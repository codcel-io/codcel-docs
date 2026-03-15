<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Excel to Code

This guide walks you through the complete process of converting an Excel spreadsheet into a generated software project using the Codcel Desktop application.

---

## Overview

The process follows five steps:

1. **Prepare** your Excel file
2. **Import** it into the Codcel Desktop app
3. **Configure** settings for your project
4. **Generate** the code
5. **Use** the generated project

---

## Step 1: Prepare Your Excel File

Before importing, ensure your Excel file follows the [Excel Guidelines](./codcel-excel-guidelines.md). Key points:

- Remove external links, comments, and embedded objects
- Delete unnecessary hidden sheets
- Ensure sheet names are unique and contain no special characters
- Save as `.xlsx` for best compatibility
- Annotate your inputs and outputs using [Codcel annotation syntax](./annotations.md)

Codcel reads your spreadsheet's formulas, cell references, and named ranges to understand the calculation logic. The cleaner your file, the better the generated code.

---

## Step 2: Import into the Desktop App

1. Open the Codcel Desktop application
2. Create a new project or open an existing one (see [Desktop Application Guide](./desktop-app.md))
3. In the sidebar, select **Business Specs**
4. Drag and drop your Excel file into the import area, or click **Browse** to select it
5. Wait for the import to complete -- a progress indicator shows the status

Your file is copied into the project's `business_specs/` directory and registered in the project configuration. The original file is not modified.

---

## Step 3: Configure Settings

Before generating code, review and adjust your project settings:

1. Open **Settings** from the sidebar
2. Set the **Decimal Separator** and **Thousands Separator** to match your Excel file's locale
3. Set the **Currency Symbol** if your spreadsheet uses currency formatting
4. Enable or disable **Strict Type Conversion** depending on how your spreadsheet handles mixed types
5. If your spreadsheet contains circular references, enable **Iterative Calculation** and set appropriate iteration limits
6. Click **Save**

For a complete list of settings and their effects, see the [Settings Reference](./settings.md).

---

## Step 4: Generate Code

1. Open **Generate Project** from the sidebar
2. Select the output targets you want:
   - The **Rust Calculation Library** is always selected -- it is the core of every generated project
   - Select additional targets such as REST API servers, web clients, or calculation libraries in other languages
   - Some targets require a Codcel account (see [Authentication](./desktop-app.md#authentication))
3. Click **Generate**
4. A progress bar tracks the generation process
5. When complete, the generated code appears in your project directory

---

## Step 5: Use the Generated Project

After generation, your project directory contains the generated source code:

```
my-project/
├── codcel.toml              # Project configuration
├── business_specs/          # Your imported Excel files
│   └── spreadsheet.xlsx
├── src/                     # Generated Rust source code
│   ├── calculations.rs      # Transpiled formulas
│   ├── model.rs             # Data model definitions
│   └── constants.rs         # Extracted constants and arrays
└── generated/               # Additional output targets
    ├── java-calculation/
    ├── restful-server/
    ├── web-client/
    └── ...
```

### Viewing Source Code in the App

After generation, new entries appear in the sidebar for each enabled output type. Click on any entry to view the generated source code directly within the application.

### Building and Running

Each generated project includes the necessary build files for its language and framework:

- **Rust projects** include `Cargo.toml` -- build with `cargo build`
- **Java/Kotlin projects** include Gradle or Maven configuration
- **Python projects** include `setup.py` or `pyproject.toml`
- **C#/Go/Swift projects** include their respective build configurations

For detailed build and run instructions for each output target, see [Output Targets](./output-targets.md).

### Testing

Each generated project includes test cases that verify the calculations match your Excel workbook. Run the tests using the standard test command for your target language (e.g., `cargo test` for Rust, `./gradlew test` for Java).

For details on interpreting test results and adding custom tests, see [Testing and Validation](./testing.md).

### Regenerating

When your Excel file changes:

1. Re-import the updated file in the Business Specs view
2. Open Generate Project and click **Generate** again
3. The generated code is updated to reflect the new spreadsheet logic

All settings and output target selections are preserved between generations.

---

## What Gets Generated

Codcel reads your Excel file and generates:

- **Calculation functions** -- each output cell or named output becomes a function in the generated code
- **Input parameters** -- annotated input cells become function parameters
- **Constants and arrays** -- static data from the spreadsheet is extracted into constants
- **Type-safe models** -- data structures that represent your inputs and outputs
- **Test documentation** -- verification that generated calculations match your Excel results
- **API endpoints** -- if a server target is selected, each calculation becomes a REST endpoint
- **Client libraries** -- if a web client target is selected, typed client code is generated for calling the API

The generated code is fully human-readable, thoroughly commented, and yours to own. It has no runtime dependency on Codcel.

---

## Next Steps

- [Desktop Application Guide](./desktop-app.md) -- detailed guide to all features of the desktop app
- [Settings Reference](./settings.md) -- full reference for all configuration options
- [UI Configuration](./ui-configuration.md) -- configure generated UIs from within Excel
- [Tables](./tables.md) -- working with structured data tables
- [Annotations](./annotations.md) -- complete guide to input, output, and table annotation syntax
- [Differences Between Codcel and Excel](./differences.md) -- understand where behaviour may differ