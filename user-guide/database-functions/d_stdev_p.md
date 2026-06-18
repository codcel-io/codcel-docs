<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DSTDEVP Function

The `DSTDEVP` function returns the **population** standard deviation (n divisor) of the numeric values in a column of a database for rows matching a criteria range. Use this when your database represents the entire population rather than a sample.

### Syntax:

    DSTDEVP(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to compute the standard deviation of. Either the 1-based column number or the header label.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DSTDEVP(A20:C28, "Score", G1:G2)` where `G1:G2` is `Group` / `X` and matched scores are `{2,4,4,4,5,5,7,9}` — returns exactly `2`.
2. `=DSTDEVP(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — returns the population standard deviation of Eng salaries.

### Usage Notes:

- Returns **#NUM!** when no numeric values match.
- Returns **0** when exactly one numeric value matches (a single value has no spread).
- Non-numeric cells in the field column are ignored.
- For sample standard deviation (n−1 divisor), use [`DSTDEV`](d_stdev.md).

> **Related**: [`DSTDEV`](d_stdev.md), [`DVARP`](d_var_p.md), [`STDEV.P`](../statistical-functions/st_dev__p.md).
