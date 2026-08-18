<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
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

Codcel provides four open-source engine crates written in Rust, plus this documentation. The
engine crates are licensed **MIT OR Apache-2.0** -- no field-of-use restrictions, no commercial
carve-outs -- and are published on crates.io, so a generated Rust project resolves them as
ordinary dependencies without needing git access:

| Crate | Role | crates.io |
|-------|------|-----------|
| `codcel-calculation-engine` | Excel-compatible formula evaluation | [link](https://crates.io/crates/codcel-calculation-engine) |
| `codcel-table-engine` | The `CodcelTable` trait -- a backend-agnostic table interface | [link](https://crates.io/crates/codcel-table-engine) |
| `codcel-parquet-engine` | Read-only `CodcelTable` implementation over Parquet | [link](https://crates.io/crates/codcel-parquet-engine) |
| `codcel-postgresql-engine` | Full CRUD `CodcelTable` implementation over PostgreSQL | [link](https://crates.io/crates/codcel-postgresql-engine) |

Generated `Cargo.toml` files pin these engines to an **exact** version, so `cargo update` cannot
move a generated calculation underneath you. See
[Engine Versions](./cli.md#engine-versions) for how to choose a different version.

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

### Codcel Parquet Engine

The read-only `CodcelTable` implementation used for [Massive Tables](./massive-tables.md). See
[Parquet Engine](#parquet-engine) below.

### Codcel PostgreSQL Engine

The full-CRUD `CodcelTable` implementation used for [CRUD Tables](./crud-tables.md). See
[PostgreSQL Engine](#postgresql-engine) below.

### Codcel Documentation

This user guide is open source and community-improvable, licensed CC BY 4.0.

Links to these repositories are available on the [Codcel website](https://codcel.io).

---

## Backend Engines

### Parquet Engine

Used for [Massive Tables](./massive-tables.md) (billions of rows, read-only).

- Implements the `CodcelTable` trait
- Uses Apache DataFusion to execute SQL queries against Parquet files
- Includes query caching (5-minute TTL) and request coalescing
- Supports sharded files (data split across multiple Parquet files)

!!! note
    Correct assembly of results spanning multiple Arrow record batches -- which happens with
    sharded tables and with aggregate or `DISTINCT` queries -- requires
    `codcel-parquet-engine` **0.1.9 or later**. Earlier versions could return rows with too many
    or too few columns in those cases. Regenerate an older project, or raise the engine version,
    to pick up the fix.
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