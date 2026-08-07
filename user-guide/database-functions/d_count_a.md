<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## DCOUNTA Function

The `DCOUNTA` function counts the non-empty cells in a column of a database for rows that match a criteria range. Unlike [`DCOUNT`](d_count.md), it counts cells of any type (numbers, text, booleans), excluding only empty cells.

### Syntax:

    DCOUNTA(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column whose non-empty cells are counted. Either the 1-based column number or the header label. May be omitted, in which case `DCOUNTA` returns the number of matched rows.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DCOUNTA(A1:E11, "Name", G1:G2)` where `G1:G2` is `Dept` / `Eng` — counts Eng rows with a non-empty Name.
2. `=DCOUNTA(A35:B41, "Qty", G1:G2)` where Qty has one numeric, one text ("TBD"), and one empty cell among matched rows — returns 2.
3. `=DCOUNTA(A1:E11, , G1:G2)` — field omitted, returns the number of matched rows.

### Usage Notes:

- Empty cells (including cells with `""`) are **not** counted.
- Use [`DCOUNT`](d_count.md) when you want to count only numeric cells.
- Returns **0** when no rows match.

> **Related**: [`DCOUNT`](d_count.md), [`COUNTA`](../statistical-functions/counta.md).
