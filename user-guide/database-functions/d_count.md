<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DCOUNT Function

The `DCOUNT` function counts the numeric cells in a column of a database for rows that match a criteria range. It is the database-style counterpart to `COUNTIF` / `COUNTIFS` restricted to numeric values.

### Syntax:

    DCOUNT(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column whose numeric cells are counted. Either the 1-based column number or the header label. May be omitted (or empty), in which case `DCOUNT` returns the number of matched rows.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DCOUNT(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — counts rows in Dept="Eng" with a numeric Salary cell.
2. `=DCOUNT(A1:E11, "Name", G1:G2)` — returns 0, because Name is text (DCOUNT counts numeric cells only).
3. `=DCOUNT(A1:E11, , G1:G2)` — field omitted, returns the count of matched rows.

### Usage Notes:

- Text and empty cells in the field column are **not** counted.
- Use [`DCOUNTA`](d_count_a.md) when you want to count non-empty cells regardless of type.
- Returns **0** when no rows match the criteria.
- Comparison operators and wildcards supported in criteria values.

> **Related**: [`DCOUNTA`](d_count_a.md), [`COUNTIF`](../conditional-functions/count_if.md).
