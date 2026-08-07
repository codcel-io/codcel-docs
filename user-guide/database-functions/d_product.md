<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## DPRODUCT Function

The `DPRODUCT` function multiplies all the numeric values in a column of a database for rows matching a criteria range.

### Syntax:

    DPRODUCT(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column whose values are multiplied. Either the 1-based column number or the header label.
- **criteria**: A range whose first row matches one or more `database` headers, with filter values in subsequent rows.

### Examples:

1. `=DPRODUCT(A35:B41, "Qty", G1:G2)` where `G1:G2` is `Item` / `A` and matched Qty values are `[2, 3, 4]` — returns `24`.
2. `=DPRODUCT(A1:E11, "Years", G1:G2)` where `G1:G2` is `Dept` / `Eng` and matched values are `[5, 3, 7, 4]` — returns `420`.

### Usage Notes:

- Returns **0** when no rows match (matches Excel behavior — note this differs from `PRODUCT([])` which returns 1).
- Non-numeric cells in the field column are ignored.
- A single zero in the matched set produces a result of 0.

> **Related**: [`PRODUCT`](../mathematical-functions/product.md), [`DSUM`](d_sum.md).
