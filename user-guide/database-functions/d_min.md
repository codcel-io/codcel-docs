<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## DMIN Function

The `DMIN` function returns the smallest numeric value in a column of a database for rows matching a criteria range. It is the database-style counterpart to `MINIFS`.

### Syntax:

    DMIN(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to find the minimum of. Either the 1-based column number or the header label.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DMIN(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — returns the lowest Eng salary.
2. `=DMIN(A1:E11, "Years", G1:G2)` where `G1:G2` is `Manager` / `TRUE` — returns the minimum years of experience among managers.

### Usage Notes:

- Returns **0** when no rows match (matches Excel behavior).
- Non-numeric cells in the field column are ignored.
- Comparison operators and wildcards supported in criteria values.

> **Related**: [`DMAX`](d_max.md), [`MINIFS`](../statistical-functions/min_ifs.md).
