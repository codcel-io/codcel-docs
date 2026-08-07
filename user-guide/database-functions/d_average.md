<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## DAVERAGE Function

The `DAVERAGE` function returns the arithmetic mean of the values in a column of a database (a labeled range) for rows matching a criteria range. It is the database-style counterpart to `AVERAGEIF` / `AVERAGEIFS`.

### Syntax:

    DAVERAGE(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to average. Either the 1-based column number or the header label (case-insensitive).
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows. AND within a row, OR across rows.

### Examples:

1. `=DAVERAGE(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Dept` / `Eng` — average salary across all Eng rows.
2. `=DAVERAGE(A1:E11, "Years", G1:G2)` — average years of experience for the same Eng group.
3. `=DAVERAGE(A1:E11, 3, G1:H2)` with `G1:H2` = `Dept` / `Salary` headers and `Eng` / `>=100` — average salary where Dept="Eng" AND Salary≥100.

### Usage Notes:

- Returns **0** when no rows match the criteria (matches Excel).
- Non-numeric cells in the field column are ignored.
- Comparison operators (`>`, `>=`, `<`, `<=`, `<>`, `=`) and wildcards (`*`, `?`) supported in criteria values.

> **Related**: [`DSUM`](d_sum.md), [`DCOUNT`](d_count.md), [`AVERAGEIF`](../conditional-functions/average_if.md).
