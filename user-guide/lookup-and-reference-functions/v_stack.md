<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# VSTACK Function

The `VSTACK` function in Excel is used to **vertically stack values into a single array**. It takes one or more arguments and places each one underneath the previous (in rows) to form a new vertical array. This function is especially useful for combining values from different ranges or constants into a row-oriented structure.

## Key Features of `VSTACK`:

- Combines values from multiple sources into a single vertical array.
- Accepts both scalar values and arrays.
- Supports dynamic arrays and automatically spills results into adjacent rows.

## Syntax:

```plaintext
VSTACK(array1, [array2], …)
```

- **array1, array2, …**: One or more arrays or values to be stacked vertically. Scalars are treated as 1×1 arrays.

## How `VSTACK` Works:

1. Each input is interpreted as an array (or converted to one).
2. Arrays are aligned **column-wise** and concatenated **row-wise**.
3. The result is a single vertical array where each input appears on a new row.
4. All inputs must have the same number of columns. Excel pads narrower rows with `#N/A`; **Codcel returns an error instead** — see *Differences from Excel* below.

## Examples:

### 1. Combine Scalar Strings Vertically:

```excel
=VSTACK("Apple", "Banana", "Cherry")
```

**Result:**
```
Apple
Banana
Cherry
```

### 2. Combine Ranges Vertically:

Assume:
- A1:A2 contains `1`, `2`
- A3:A4 contains `3`, `4`

```excel
=VSTACK(A1:A2, A3:A4)
```

**Result:**
```
1
2
3
4
```

### 3. Stack Several Arrays of Differing Heights:

```excel
=VSTACK({"A","B"}, {"C","D";"E","F"})
```

**Result:**
```
A   B
C   D
E   F
```

The arrays may have different numbers of rows, but they must have the same number of columns.

## Notes:

- `VSTACK` is available in Excel 365 and Excel 2021.
- It returns a **spilled array** that resizes automatically.
- In Codcel, arrays with mismatched column counts return an error rather than a spilled result.

## Differences from Excel:

Excel pads ragged input with `#N/A`, so `=VSTACK(A1:C1, "x")` returns a row of `x` / `#N/A` / `#N/A`. Codcel returns the error `VSTACK: All arrays must have the same number of columns` instead — an `#N/A` cell cannot be represented in a numeric spill in generated code, so an explicit error is preferred over an unrepresentable value.

Note that a scalar is treated as a 1x1 array, so scalars can only be combined with arrays that are also one column wide. `=VSTACK("Apple","Banana","Cherry")` works; `=VSTACK(A1:C1, "x")` does not.

## Applications:

- **Data Merging**: Combine multiple datasets or result tables into one unified vertical list.
- **Table Construction**: Build custom tables by stacking headers, rows, and footers.
- **Dynamic Reporting**: Assemble structured reports from multiple calculated ranges.

> **Tip:** Use `HSTACK` if you need to join arrays **horizontally** instead of vertically.