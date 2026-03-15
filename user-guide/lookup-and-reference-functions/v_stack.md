<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
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
4. Arrays with different column counts are padded with blanks where needed.

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

### 3. Stack Mixed Arrays and Scalars:

```excel
=VSTACK({"A","B"}, {"C";"D"}, "E")
```

**Result:**
```
A   B
C
D
E
```

Here, `"E"` is appended as a new row.

## Notes:

- `VSTACK` is available in Excel 365 and Excel 2021.
- It returns a **spilled array** that resizes automatically.
- Mismatched column widths are padded with empty cells to maintain alignment.

## Applications:

- **Data Merging**: Combine multiple datasets or result tables into one unified vertical list.
- **Table Construction**: Build custom tables by stacking headers, rows, and footers.
- **Dynamic Reporting**: Assemble structured reports from multiple calculated ranges.

> **Tip:** Use `HSTACK` if you need to join arrays **horizontally** instead of vertically.