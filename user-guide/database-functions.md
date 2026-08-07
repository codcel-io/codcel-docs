<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Database Functions

Database functions (also called "D-functions") aggregate or look up values in a tabular range using a separate criteria range to express filters. They are conceptually similar to `SUMIFS` / `AVERAGEIFS` / `COUNTIFS`, but criteria live in their own labeled range rather than being passed as inline `(range, value)` pairs.

All database functions share the same three-argument signature:

    DFUNC(database, field, criteria)

- **database** — a contiguous range whose first row contains column labels.
- **field** — either the 1-based column number, or the header label as text (case-insensitive).
- **criteria** — a range whose first row matches one or more `database` headers. Cells in the same criteria row AND together; multiple criteria rows OR together. Wildcards (`*`, `?`) and comparison prefixes (`>`, `>=`, `<`, `<=`, `<>`, `=`) are supported in criteria values.

This list contains the database functions that are currently supported by Codcel.


## D

### [DAVERAGE](./database-functions/d_average.md)
Returns the arithmetic mean of the values in a column for rows matching the criteria. Empty match returns 0.

- **Example:** `=DAVERAGE(A1:E11, "Salary", G1:G2)`

### [DCOUNT](./database-functions/d_count.md)
Counts the numeric cells in a column for rows matching the criteria. Text and empty cells are excluded.

- **Example:** `=DCOUNT(A1:E11, "Salary", G1:G2)`

### [DCOUNTA](./database-functions/d_count_a.md)
Counts the non-empty cells (any type) in a column for rows matching the criteria.

- **Example:** `=DCOUNTA(A1:E11, "Name", G1:G2)`

### [DGET](./database-functions/d_get.md)
Returns the value at the unique matching row's entry in the specified column. Returns `#NUM!` for zero matches, `#VALUE!` for multiple matches.

- **Example:** `=DGET(A1:E11, "Salary", G1:G2)`

### [DMAX](./database-functions/d_max.md)
Returns the maximum numeric value in a column for rows matching the criteria. Empty match returns 0.

- **Example:** `=DMAX(A1:E11, "Salary", G1:G2)`

### [DMIN](./database-functions/d_min.md)
Returns the minimum numeric value in a column for rows matching the criteria. Empty match returns 0.

- **Example:** `=DMIN(A1:E11, "Salary", G1:G2)`

### [DPRODUCT](./database-functions/d_product.md)
Multiplies the numeric values in a column for rows matching the criteria. Empty match returns 0.

- **Example:** `=DPRODUCT(A35:B41, "Qty", G1:G2)`

### [DSTDEV](./database-functions/d_stdev.md)
Returns the sample standard deviation (n−1 divisor) of the numeric values in a column for rows matching the criteria. Fewer than 2 values returns `#DIV/0!`.

- **Example:** `=DSTDEV(A1:E11, "Salary", G1:G2)`

### [DSTDEVP](./database-functions/d_stdev_p.md)
Returns the population standard deviation (n divisor) of the numeric values in a column for rows matching the criteria. Zero values returns `#NUM!`.

- **Example:** `=DSTDEVP(A1:E11, "Salary", G1:G2)`

### [DSUM](./database-functions/d_sum.md)
Sums the values in a column for rows matching the criteria. Empty match returns 0.

- **Example:** `=DSUM(A1:E11, "Salary", G1:G2)`

### [DVAR](./database-functions/d_var.md)
Returns the sample variance (n−1 divisor) of the numeric values in a column for rows matching the criteria. Fewer than 2 values returns `#DIV/0!`.

- **Example:** `=DVAR(A1:E11, "Salary", G1:G2)`

### [DVARP](./database-functions/d_var_p.md)
Returns the population variance (n divisor) of the numeric values in a column for rows matching the criteria. Zero values returns `#NUM!`.

- **Example:** `=DVARP(A1:E11, "Salary", G1:G2)`
