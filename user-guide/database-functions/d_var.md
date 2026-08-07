<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## DVAR Function

The `DVAR` function returns the **sample** variance (n−1 divisor) of the numeric values in a column of a database for rows matching a criteria range.

### Syntax:

    DVAR(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to compute the variance of. Either the 1-based column number or the header label.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DVAR(A20:C28, "Score", G1:G2)` where matched scores are `{2,4,4,4,5,5,7,9}` — returns approximately `4.5714` (32/7).
2. `=DVAR(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — returns the sample variance of Eng salaries.

### Usage Notes:

- Returns **#DIV/0!** when fewer than 2 numeric values match (sample variance is undefined for n<2).
- `DVAR` and [`DSTDEV`](d_stdev.md) are related: `DSTDEV² = DVAR`.
- For population variance (n divisor), use [`DVARP`](d_var_p.md).

> **Related**: [`DVARP`](d_var_p.md), [`DSTDEV`](d_stdev.md), [`VAR.S`](../statistical-functions/var__s.md).
