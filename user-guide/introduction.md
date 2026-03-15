<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Introduction

## What is Codcel?

Codcel is a platform that transforms Excel spreadsheets into production-ready software. It reads your annotated Excel workbooks and automatically generates source code in languages such as **Rust, Python, Java, C#, Go, Swift, Kotlin, JavaScript/TypeScript**, and more.

Codcel bridges the gap between business logic -- often captured in Excel -- and production software, enabling businesses and developers to move from prototype spreadsheets to maintainable, deployable code.

## Who is Codcel For?

- **Business analysts and domain experts** who build complex models in Excel and need them deployed as software
- **Development teams** looking to eliminate the manual, error-prone process of translating spreadsheet logic into code
- **Organisations** that want to maintain a single source of truth in Excel while generating production-grade applications

## What Does Codcel Generate?

From a single annotated Excel workbook, Codcel can generate:

- **Calculation engines** -- the core logic from your spreadsheet, converted into performant code
- **REST APIs** -- ready-to-deploy web services that expose your calculations as endpoints
- **Table engines** -- high-performance columnar storage with CRUD functionality
- **UI components** -- user interfaces for interacting with your calculations
- **MCP servers** -- integration points for broader system connectivity
- **Test documentation** -- verifying that generated calculations match your Excel results

## Why Not Convert Manually?

Manually translating Excel formulas into code is a common approach but comes with significant risks:

1. **Loss of nuance** -- complex formulas or VBA macros may be misinterpreted or overlooked
2. **Implicit assumptions** -- Excel performs operations like cell type conversions that other languages do not
3. **Rounding errors** -- different rounding approaches between Excel and programming languages can lead to discrepancies
4. **Performance issues** -- a manually optimised Excel formula may not translate well to a high-demand web service
5. **Inadequate testing** -- missed test scenarios can lead to errors in edge cases
6. **Maintenance burden** -- future formula updates require repeating the entire translation process

Codcel eliminates these risks by automating the conversion process with consistency, accuracy, and full traceability back to the original Excel workbook.

## Key Benefits

- **Accuracy** -- automated conversion preserves the exact logic of your Excel formulas
- **Speed** -- generate production code in minutes, not weeks
- **Consistency** -- every conversion follows the same process, reducing human error
- **Scalability** -- handle large Excel files with hundreds of formulas efficiently
- **Maintainability** -- when the Excel logic changes, regenerate the code
- **Full ownership** -- the generated code is yours, fully readable, and independent of Codcel at runtime

## Getting Started

To begin using Codcel:

1. [Download Codcel](https://codcel.io/download) for your platform (Windows, macOS, Linux)
2. Prepare your Excel file following the [Excel Guidelines](./codcel-excel-guidelines.md)
3. Import your spreadsheet into the Codcel Desktop app
4. [Annotate](./annotations.md) your inputs, outputs, tables, and UI elements
5. Generate your project

For detailed guidance on preparing your Excel files, see the [Excel Guidelines](./codcel-excel-guidelines.md).
For annotation syntax, see the [Annotations](./annotations.md) guide.