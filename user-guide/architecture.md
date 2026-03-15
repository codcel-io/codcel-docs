<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Architecture

This page explains how Codcel's components work together to transform Excel spreadsheets into production-ready software.

---

## Component Overview

Codcel consists of several components that work together:

```
+-------------------+
|  Excel Workbook   |
+-------------------+
         |
         v
+-------------------+
|    Transpiler     |  Reads formulas, resolves references, generates code
+-------------------+
         |
         v
+-------------------+     +----------------------------+
|  Generated Code   |---->|  Codcel Calculation Engine  |  (open source)
|                   |     |  Excel-compatible formulas   |
|  - Calculations   |     +----------------------------+
|  - Models         |
|  - Servers        |     +----------------------------+
|  - Web Clients    |---->|  Codcel Table Engine        |  (open source)
|  - CLI / MCP      |     |  Async trait for table ops   |
+-------------------+     +----------------------------+
                                    |
                          +---------+---------+
                          |                   |
                          v                   v
                  +---------------+   +-----------------+
                  | Parquet Engine|   | PostgreSQL Engine|
                  | (read-only)   |   | (CRUD)          |
                  +---------------+   +-----------------+
```

---

## Open-Source Components

Codcel provides three open-source libraries written in Rust:

### Codcel Calculation Engine

The core formula engine that implements Excel-compatible calculations. It supports hundreds of functions across mathematical, statistical, financial, text, date/time, engineering, logical, and lookup categories.

Generated code depends on this engine at runtime. The engine handles:

- Function evaluation (500+ Excel functions)
- Type conversions between numbers, text, booleans, dates, and errors
- Excel-compatible rounding and precision
- Array and matrix operations
- Iterative calculation for circular references

### Codcel Table Engine

A Rust trait (`CodcelTable`) that defines a standard interface for table operations. This trait is implemented by both the Parquet Engine and the PostgreSQL Engine, allowing generated code to work with different backends through the same interface.

The trait defines:

- **Lookup functions:** VLOOKUP, HLOOKUP, XLOOKUP, LOOKUP
- **Matching functions:** MATCH, XMATCH
- **Access functions:** INDEX, FILTER, SELECT_ALL
- **CRUD functions:** ADD_ROW, READ_ROW, UPDATE_ROW, DELETE_ROW

### Codcel Documentation

This user guide is open source and community-improvable.

Links to these repositories are available on the [Codcel website](https://codcel.io).

---

## Backend Engines

### Parquet Engine

Used for [Massive Tables](./massive-tables.md) (billions of rows, read-only).

- Implements the `CodcelTable` trait
- Uses Apache DataFusion to execute SQL queries against Parquet files
- Includes query caching (5-minute TTL) and request coalescing
- Supports sharded files (data split across multiple Parquet files)
- Read-only -- CRUD operations are not available

### PostgreSQL Engine

Used for [CRUD Tables](./crud-tables.md) (mutable data with create/read/update/delete).

- Implements the `CodcelTable` trait
- Uses connection pooling for efficient database access
- Supports parameterised queries for SQL injection protection
- Handles type mapping between Excel types and PostgreSQL column types

---

## Code Generation Pipeline

When you generate a project, the transpiler processes your Excel workbook in this order:

1. **Load:** Read the Excel file, extract formulas, cell values, named ranges, and configuration sheets
2. **Analyse:** Build a dependency graph, detect circular references, resolve cell references
3. **Transpile:** Generate the Rust Calculation Library (always)
4. **Generate targets:** For each selected output target, apply language-specific templates to produce buildable projects

Each generated project is self-contained with its own build configuration, dependencies, and tests.

---

## Runtime Architecture

At runtime, the generated code follows one of these patterns:

### Calculation Library (embedded)

```
Your Application --> Generated Calculation Library --> Codcel Calculation Engine
```

Your application calls the generated library directly. No network involved.

### REST Server + Client

```
Web Client --> HTTP --> REST Server --> Generated Calculation --> Codcel Calculation Engine
                                                             --> Codcel Table Engine --> Parquet / PostgreSQL
```

The server exposes calculations as HTTP endpoints. Clients call these endpoints with JSON payloads.

### Fullstack UI

```
Browser --> Dioxus App (server + client) --> Generated Calculation --> Codcel Calculation Engine
```

A single application serves both the UI and the calculation logic.

### MCP Server

```
AI Assistant (e.g., Claude) --> MCP Protocol --> MCP Server --> Generated Calculation --> Codcel Calculation Engine
```

AI assistants call your calculations as tools.

---

## See Also

- [Output Targets](./output-targets.md) -- detailed guide to each generated target
- [Settings Reference](./settings.md) -- configuration options
- [Excel to Code](./excel-to-code.md) -- the complete workflow