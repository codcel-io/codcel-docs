<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# HSTACK Function

The `HSTACK` function in Excel is used to **horizontally stack values into a single array**. It takes one or more arguments and places each one side-by-side (in columns) to form a new horizontal array. This is particularly useful for combining values from different ranges or constants into a single row-oriented structure.

## Key Features of `HSTACK`:

- Combines values from multiple sources into a single horizontal array.
- Works with both scalar values and arrays.
- Supports dynamic arrays and spills results into adjacent columns.

## Syntax:

```plaintext
HSTACK(array1, [array2], …)
```

- **array1, array2, …**: One or more arrays or values to be stacked horizontally. Scalars are treated as 1×1 arrays.

## How `HSTACK` Works:

1. Each input is evaluated and converted into an array if necessary.
2. Arrays are aligned **row-wise** and concatenated **column-wise**.
3. The final result is a single horizontal array where each input is placed to the right of the previous one.
4. All inputs must have the same number of rows. Excel pads shorter arrays with `#N/A`; **Codcel returns an error instead** — see *Differences from Excel* below.

## Examples:

### 1. Combine Scalar Strings:

```excel
=HSTACK("Apple", "Banana", "Cherry")
```

**Result:**
```
Apple   Banana   Cherry
```

### 2. Combine Ranges Horizontally:

Assume:
- A1:A2 contains `1`, `2`
- B1:B2 contains `3`, `4`

```excel
=HSTACK(A1:A2, B1:B2)
```

**Result:**
```
1   3
2   4
```

### 3. Stack Arrays of Differing Widths:

```excel
=HSTACK({"A";"B"}, {"C","D";"E","F"})
```

**Result:**
```
A   C   D
B   E   F
```

The arrays may have different numbers of columns, but they must have the same number of rows.

## Notes:

- `HSTACK` is available in Excel 365 and Excel 2021.
- It automatically resizes the result (spills) to fit the array.
- In Codcel, arrays with mismatched row counts return an error rather than a spilled result.

## Differences from Excel:

Excel pads ragged input with `#N/A`, so `=HSTACK(1, A1:A3)` returns `1` / `#N/A` / `#N/A`. Codcel returns the error `HSTACK: All arrays must have the same number of rows` instead — an `#N/A` cell cannot be represented in a numeric spill in generated code, so an explicit error is preferred over an unrepresentable value.

Note that a scalar is treated as a 1x1 array, so scalars can only be combined with arrays that are also one row tall. `=HSTACK("Apple","Banana","Cherry")` and `=HSTACK(A1:B1, C1)` both work; `=HSTACK(1, A1:A3)` does not.

## Applications:

- **Dynamic Table Creation**: Combine multiple columns of data into a single structured array.
- **Data Reshaping**: Rearrange vertical or mixed arrays into horizontal format.
- **Report Generation**: Build formatted output ranges by joining different data sources.

> **Tip:** Use `VSTACK` if you want to stack values **vertically** instead of horizontally.