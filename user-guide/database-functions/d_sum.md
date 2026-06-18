<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DSUM Function

The `DSUM` function sums the values in a column of a database (a labeled range) for rows that match a criteria range. It's the database-style counterpart to `SUMIF` / `SUMIFS`, with criteria specified as a separate labeled range rather than inline.

### Syntax:

    DSUM(database, field, criteria)

- **database**: The range of cells that makes up the list or database. The first row must contain column labels (headers).
- **field**: The column to sum. Either the 1-based column number, or the header label as text (case-insensitive).
- **criteria**: A range that contains the conditions. Its first row holds header labels matching one or more `database` headers; subsequent rows hold the filter values. Cells in the same row AND together; multiple rows OR together.

### Examples:

1. `=DSUM(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — sums salaries of all rows whose Dept equals "Eng".
2. `=DSUM(A1:E11, 3, G1:G2)` — same as above, using the column index `3` instead of the header label `"Salary"`.
3. `=DSUM(A1:E11, "Salary", G1:H2)` where `G1:H2` is `Dept` / `Salary` headers and `Eng` / `>=100` — sums salaries where Dept="Eng" AND Salary≥100.

### Usage Notes:

- Returns **0** when no rows match the criteria (matches Excel behavior).
- Comparison operators in criteria values: `>`, `>=`, `<`, `<=`, `<>`, `=` (or no prefix for equality).
- Wildcards `*` (any sequence) and `?` (single character) are supported in equality criteria.
- Non-numeric cells in the field column are ignored.
- String comparisons are case-insensitive.

> **Related**: [`DAVERAGE`](d_average.md), [`DCOUNT`](d_count.md), [`SUMIF`](../conditional-functions/sum_if.md), [`SUMIFS`](../mathematical-functions/sum_ifs.md).
