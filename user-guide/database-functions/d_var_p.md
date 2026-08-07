<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## DVARP Function

The `DVARP` function returns the **population** variance (n divisor) of the numeric values in a column of a database for rows matching a criteria range.

### Syntax:

    DVARP(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to compute the variance of. Either the 1-based column number or the header label.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DVARP(A20:C28, "Score", G1:G2)` where matched scores are `{2,4,4,4,5,5,7,9}` — returns exactly `4`.
2. `=DVARP(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — returns the population variance of Eng salaries.

### Usage Notes:

- Returns **#NUM!** when no numeric values match.
- Returns **0** when exactly one numeric value matches (no spread).
- `DVARP` and [`DSTDEVP`](d_stdev_p.md) are related: `DSTDEVP² = DVARP`.
- For sample variance (n−1 divisor), use [`DVAR`](d_var.md).

> **Related**: [`DVAR`](d_var.md), [`DSTDEVP`](d_stdev_p.md), [`VAR.P`](../statistical-functions/var__p.md).
