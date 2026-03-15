<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Big Data

Codcel supports a tiered approach to data, allowing you to work with datasets ranging from a few rows to billions of rows. The right table type depends on the size and nature of your data.

---

## Table Tiers

| Table Type | Row Limit | Storage | Formulas | CRUD |
|------------|-----------|---------|----------|------|
| [Small Tables](./small-tables.md) | Thousands | In-memory | Yes | No |
| [Large Tables](./large-tables.md) | 1,048,576 | Excel sheet | No (frozen at import) | No |
| [Massive Tables](./massive-tables.md) | Billions | CSV / Parquet | No (frozen at import) | No |
| [CRUD Tables](./crud-tables.md) | Unlimited | PostgreSQL | No | Yes |

### When to Use Each

- **Small Tables** -- when your data fits comfortably in a sheet and you need formulas that reference input parameters within the table rows. Best for lookup data, configuration tables, and reference data with computed columns.

- **Large Tables** -- when your data fills up to a full Excel sheet (1,048,576 rows) but does not require formulas that change based on inputs. The table must occupy its own sheet with a `T_` prefix name.

- **Massive Tables** -- when your data exceeds Excel's row limit. Provide the data as a CSV file alongside your Excel workbook. The data is stored in Parquet columnar format and queried using SQL, delivering fast lookups even on billions of rows.

- **CRUD Tables** -- when you need to create, read, update, and delete rows at runtime. CRUD tables are backed by PostgreSQL and are ideal for application data that changes over time.

---

## How Codcel Handles Large Data

For massive tables, Codcel uses a pipeline:

1. **CSV Import** -- your CSV data is read during code generation
2. **Parquet Conversion** -- data is converted to Apache Parquet, a columnar storage format optimised for analytical queries
3. **SQL Query Engine** -- at runtime, the generated code uses Apache DataFusion to execute SQL queries against the Parquet files
4. **Caching** -- query results are cached for 5 minutes, and concurrent identical queries are coalesced into a single execution

This architecture allows Codcel-generated applications to handle datasets of any size while maintaining fast query response times.

---

## Supported Functions on Large and Massive Tables

The following Excel functions work on all table types:

- **VLOOKUP** -- vertical lookup
- **HLOOKUP** -- horizontal lookup
- **XLOOKUP** -- advanced lookup
- **LOOKUP** -- simplified lookup
- **INDEX** -- direct access by position
- **MATCH** -- find position of a value
- **XMATCH** -- extended match
- **FILTER** -- conditional filtering

For details on table-specific functions, see [Table Functions](./table-functions.md).

---

## Performance at Scale

For a real-world demonstration of Codcel handling 1 billion rows of data, see the [One Billion Row Challenge](./one-billion-row-challenge.md). Key results:

- **1 billion rows** (12 GB CSV file)
- **8 seconds** for the first query
- **1.5 seconds** for cached queries

---

## See Also

- [Small Tables](./small-tables.md)
- [Large Tables](./large-tables.md)
- [Massive Tables](./massive-tables.md)
- [CRUD Tables](./crud-tables.md)
- [Table Functions](./table-functions.md)
- [One Billion Row Challenge](./one-billion-row-challenge.md)