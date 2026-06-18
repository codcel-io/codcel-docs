<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DMAX Function

The `DMAX` function returns the largest numeric value in a column of a database for rows matching a criteria range. It is the database-style counterpart to `MAXIFS`.

### Syntax:

    DMAX(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to find the maximum of. Either the 1-based column number or the header label.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DMAX(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — returns the highest Eng salary.
2. `=DMAX(A1:E11, "Years", G1:G2)` where `G1:G2` is `Manager` / `TRUE` — returns the maximum years of experience among managers.

### Usage Notes:

- Returns **0** when no rows match (matches Excel behavior).
- Non-numeric cells in the field column are ignored.
- Comparison operators and wildcards supported in criteria values.

> **Related**: [`DMIN`](d_min.md), [`MAXIFS`](../statistical-functions/max_ifs.md).
