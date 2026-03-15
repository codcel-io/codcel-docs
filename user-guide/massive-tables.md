<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Massive Tables

If you require tables that contain more than 1,048,576 rows -- up to billions of rows -- Codcel can handle them using external CSV files backed by the high-performance Parquet columnar storage engine.

---

## Overview

Excel has a limit of 1,048,576 rows per sheet. For datasets that exceed this limit, Codcel allows you to provide the data as a separate CSV file. During code generation, the CSV data is converted to Parquet format and queried using the Apache DataFusion SQL engine, enabling efficient lookups and filtering across billions of rows.

Massive tables are **read-only**. You can use lookup and filtering functions on them, but CRUD operations (add, update, delete) are not supported. For tables that need CRUD operations, see [CRUD Tables](./crud-tables.md).

---

## How It Works

### 1. Create a CSV File

Prepare your data as a CSV file. The file must be UTF-8 encoded.

Example `T_Measurements.csv`:

```csv
Hamburg;12.0
Berlin;8.5
Munich;15.3
Hamburg;11.2
Berlin;7.8
```

### 2. Name the CSV File to Match Your Excel Sheet

The CSV file name must match an Excel sheet name that uses the `T_` prefix. For example:

| Excel Sheet Name | CSV File Name |
|------------------|---------------|
| `T_Measurements` | `T_Measurements.csv` |
| `T_Addresses` | `T_Addresses.csv` |
| `T_Transactions` | `T_Transactions.csv` |

The Excel sheet defines the table's schema (column headers in row 1). The CSV file provides the actual data. The same rules as [Large Tables](./large-tables.md) apply to the Excel sheet: the table must start at column A, row 1 contains column headers, and one table per sheet.

### 3. Configure CSV Settings

In the desktop app's **Settings** view (or in `codcel.toml`), configure how your CSV files are parsed:

| Setting | Default | Description |
|---------|---------|-------------|
| CSV Has Header | `false` | Whether the first row of the CSV is a header row |
| CSV Delimiter | `,` | The character that separates fields (e.g., `,`, `;`, `\t`) |

### 4. Reference the Table in Your Formulas

Use standard Excel lookup and filtering functions to query the massive table. Codcel supports the following functions on massive tables:

- **VLOOKUP** -- vertical lookup by key
- **HLOOKUP** -- horizontal lookup
- **XLOOKUP** -- advanced lookup with flexible match and search modes
- **LOOKUP** -- simplified lookup
- **INDEX** -- direct cell or row access
- **MATCH** -- find position of a value
- **XMATCH** -- extended match with advanced modes
- **FILTER** -- conditional row filtering

These functions work the same way as on regular tables, but are executed as optimised SQL queries against the Parquet data rather than scanning rows in memory.

---

## Match and Search Modes

When using XLOOKUP or XMATCH on massive tables, the following match and search modes are supported:

### Match Modes

| Mode | Description |
|------|-------------|
| `0` | Exact match only |
| `-1` | Exact match, or next smallest value |
| `1` | Exact match, or next largest value |
| `2` | Wildcard matching (`*` and `?`) |

### Search Modes

| Mode | Description |
|------|-------------|
| `1` | Search from first to last (default) |
| `-1` | Search from last to first |
| `2` | Binary search (data must be sorted ascending) |
| `-2` | Binary search (data must be sorted descending) |

---

## Performance

### Query Caching

To avoid re-executing expensive queries, the Parquet engine caches query results with a **5-minute time-to-live (TTL)**. Repeated lookups with the same parameters return instantly from cache.

### Request Coalescing

When multiple concurrent requests execute the same query (common in server deployments), only one query is actually executed. Other identical requests wait for and share the result, significantly reducing load on large datasets.

### Tips for Best Performance

- Use exact match mode (`0`) when possible -- it generates the most efficient queries
- Structure your data so that frequently queried columns appear early in the table
- For repeated queries with varying parameters, the caching system handles optimisation automatically

---

## Supported Data Types

The Parquet engine supports the following column types:

| Type | Description |
|------|-------------|
| String | Text values |
| Integer | 32-bit integer values |
| Double | 64-bit floating-point values |
| Date | Date values |
| Timestamp | Date and time values |
| Boolean | True/false values |

---

## Limitations

- **Read-only**: Massive tables do not support CRUD operations (`ADD_ROW`, `UPDATE_ROW`, `DELETE_ROW`, `READ_ROW`). For mutable tables, use [CRUD Tables](./crud-tables.md) with PostgreSQL.
- **No formulas in data**: Like large tables, CSV data is static. Formulas in the Excel sheet are computed at import time and cannot reference input parameters.
- **Range parameters ignored**: When calling VLOOKUP or similar functions, the cell range parameter in the formula is ignored -- the query always operates on the entire table.

---

## Worked Example

For a complete worked example using massive tables with 1 billion rows of data, see the [One Billion Row Challenge](./one-billion-row-challenge.md).

---

## See Also

- [Tables Overview](./tables.md) -- comparison of all table types
- [Large Tables](./large-tables.md) -- tables up to 1,048,576 rows within Excel
- [Small Tables](./small-tables.md) -- in-memory tables with formula support
- [CRUD Tables](./crud-tables.md) -- mutable tables backed by PostgreSQL
- [Big Data](./big-data.md) -- overview of Codcel's data scaling strategy