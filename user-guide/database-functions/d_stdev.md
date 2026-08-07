<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## DSTDEV Function

The `DSTDEV` function returns the **sample** standard deviation (n−1 divisor) of the numeric values in a column of a database for rows matching a criteria range. Use this when your database is treated as a sample of a larger population.

### Syntax:

    DSTDEV(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to compute the standard deviation of. Either the 1-based column number or the header label.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DSTDEV(A20:C28, "Score", G1:G2)` where `G1:G2` is `Group` / `X` and matched scores are `{2,4,4,4,5,5,7,9}` — returns approximately `2.138`.
2. `=DSTDEV(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — returns the sample standard deviation of Eng salaries.

### Usage Notes:

- Returns **#DIV/0!** when fewer than 2 numeric values match (sample standard deviation is undefined for n<2).
- Non-numeric cells in the field column are ignored.
- For population standard deviation (n divisor), use [`DSTDEVP`](d_stdev_p.md).

> **Related**: [`DSTDEVP`](d_stdev_p.md), [`DVAR`](d_var.md), [`STDEV.S`](../statistical-functions/st_dev__s.md).
