<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Codcel Documentation

Welcome to the official documentation for **Codcel** -- a platform that transforms Excel spreadsheets into **real, production-ready software**.

Codcel reads your annotated Excel workbooks and generates:

- **Source code** in languages such as **Rust, Python, Java, C#, Go, Swift, Kotlin, JavaScript/TypeScript**, and more
- **Calculation engines** (Codcel Calculation Engine -- open source, Rust)
- **Table engines** with CRUD functionality and high-performance columnar storage (Codcel Table Engine -- open source, Rust)
- **REST APIs**, **UI components**, and **MCP servers**
- Fully-structured, human-readable code your team owns

Codcel allows businesses and developers to move instantly from prototype spreadsheets to maintainable software -- while keeping complete control of source code.

---

## Official Website

Visit the main website for product details, downloads, pricing, and examples:

**https://codcel.io**

---

## Download Codcel

The Codcel Desktop app (Windows, macOS, Linux) can be downloaded from the Codcel website.
The desktop app runs entirely locally and is used to import spreadsheets, annotate them, and generate software projects.

---

## Open-Source Projects

Codcel provides several open-source components written in Rust:

- **[Codcel Calculation Engine](https://github.com/codcel-io/codcel-calculation-engine)**
  Excel-compatible formula engine supporting hundreds of functions.

- **[Codcel Table Engine](https://github.com/codcel-io/codcel-table-engine)**
  High-performance columnar table engine used by generated code.

- **[Codcel Parquet Engine](https://github.com/codcel-io/codcel-parquet-engine)**
  Read and write Apache Parquet files for efficient big-data storage.

- **[Codcel PostgreSQL Engine](https://github.com/codcel-io/codcel-postgresql-engine)**
  Connect generated applications directly to PostgreSQL databases.

- **[Codcel Documentation](https://github.com/codcel-io/codcel-docs)** (this site)
  All documentation is open source and community-improvable.

---

## How This Documentation Is Structured

This documentation covers:

- How to use the Codcel desktop app and CLI
- How Codcel interprets Excel spreadsheets, annotations, and settings
- What output targets are available — calculation libraries, REST servers, web clients, fullstack UI, and integrations (OpenAPI, CLI, MCP, JNI, FFI)
- How tables, CRUD operations, and named ranges work
- Excel concepts like dynamic arrays, functional programming, and circular references
- Reference documentation for all supported Excel functions
- How Codcel handles large datasets (Big Data + One Billion Row Challenge)
- Differences between Codcel and Excel
- Troubleshooting with error and warning codes
- Architecture overview

Use this index as a guide to every major topic.

---

## Documentation Index

### Getting Started
- [Introduction](./introduction.md)
- [Desktop Application Guide](./desktop-app.md)
- [Excel to Code](./excel-to-code.md)
- [Excel Guidelines](./codcel-excel-guidelines.md)
- [Annotations](./annotations.md)
- [Settings Reference](./settings.md)
- [Runtime Formatting](./runtime-formatting.md)
- [Command Line Interface](./cli.md)
- [Testing and Validation](./testing.md)

### Output Targets
- [Output Targets Overview](./output-targets.md)
- [Calculation Libraries](./output-targets/calculation-libraries.md)
- [REST Servers](./output-targets/servers.md)
- [Web Clients](./output-targets/web-clients.md)
- [Fullstack UI](./output-targets/fullstack-ui.md)
- [Integrations](./output-targets/integrations.md) (OpenAPI, CLI, MCP, JNI, FFI)
- [Excel Python Interface](./output-targets/excel-python-interface.md) (xlwings, .xlsm workbooks)
- [Excel Web Client Python Interface](./output-targets/excel-web-client-python-interface.md) (xlwings, .xlsm workbooks via REST API)

### Tables & Data
- [Tables](./tables.md)
- [Table Functions](./table-functions.md)
- [CRUD Tables](./crud-tables.md)
- [Named Ranges](./named-ranges.md)

### Excel Concepts
- [Dynamic Arrays](./dynamic-arrays.md)
- [Functional Programming](./functional-programming.md)
- [Circular References](./circular-references.md)

### Excel Function References
- [Alphabetical Function List](./alphabetical-functions.md)
- [Mathematical Functions](./mathematical-functions.md)
- [Statistical Functions](./statistical-functions.md)
- [Text Functions](./text-functions.md)
- [Conditional Functions](./conditional-functions.md)
- [Engineering Functions](./engineering-functions.md)
- [Financial Functions](./financial-functions.md)
- [Logical Functions](./logical-functions.md)
- [Compatibility Functions](./compatibility-functions.md)
- [Date & Time Functions](./date-time-functions.md)
- [Lookup & Reference Functions](./lookup-and-reference-functions.md)
- [Information Functions](./information-functions.md)

### UI & Configuration
- [Settings Reference](./settings.md)
- [UI Configuration](./ui-configuration.md)

### Differences
- [Differences Between Codcel and Excel](./differences.md)

### Performance & Large Data
- [Big Data](./big-data.md)
- [One Billion Row Challenge](./one-billion-row-challenge.md)

### Troubleshooting
- [Error and Warning Codes](./error-codes.md)

### Architecture
- [Architecture Overview](./architecture.md)