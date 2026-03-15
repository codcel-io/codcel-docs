<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# CHOOSEROWS Function

The `CHOOSEROWS` function in Excel is used to **return specified rows from an array or range**. It allows you to select one or more rows by their index numbers and returns them in the order specified. This is particularly useful for rearranging row order, extracting specific rows, or duplicating rows within a dataset.

## Key Features of `CHOOSEROWS`:

- Extracts specific rows from an array or range by index.
- Returns rows in any order you specify.
- Supports negative indices to count from the bottom.
- Can duplicate rows by specifying the same index multiple times.
- Works seamlessly with other dynamic array functions.

## Syntax:

```plaintext
CHOOSEROWS(array, row_num1, [row_num2], …)
```

- **array**: The array or range from which to return rows.
- **row_num1**: The index of the first row to return. Use positive numbers to count from the top (1 = first row) or negative numbers to count from the bottom (-1 = last row).
- **row_num2, …** (optional): Additional row indices to return.

## How `CHOOSEROWS` Works:

1. Takes the input array and identifies the rows at each specified index.
2. Positive indices count from the top (1 is the first row).
3. Negative indices count from the bottom (-1 is the last row).
4. Returns the selected rows in the order specified.
5. If an index is out of range, Excel returns a `#VALUE!` error.

## Examples:

### 1. Extract a Single Row:

Given a range A1:D5 with data:
```excel
=CHOOSEROWS(A1:D5, 2)
```

**Result:**
```
Returns only the second row from the range
```

### 2. Extract Multiple Rows:

```excel
=CHOOSEROWS(A1:D5, 1, 3, 5)
```

**Result:**
```
Returns the first, third, and fifth rows from the range
```

### 3. Reorder Rows:

```excel
=CHOOSEROWS(A1:D5, 5, 3, 1, 2, 4)
```

**Result:**
```
Returns rows in order: 5, 3, 1, 2, 4 (reversed and rearranged)
```

### 4. Use Negative Indices:

```excel
=CHOOSEROWS(A1:D5, -1, -2)
```

**Result:**
```
Returns the last row and second-to-last row (rows 5 and 4)
```

### 5. Duplicate a Row:

```excel
=CHOOSEROWS(A1:D5, 1, 2, 2, 3)
```

**Result:**
```
Returns rows 1, 2, 2, 3 (row 2 appears twice)
```

### 6. Extract from an Array Constant:

```excel
=CHOOSEROWS({1,2,3;4,5,6;7,8,9}, 1, 3)
```

**Result:**
```
1   2   3
7   8   9
```

(Returns the first and third rows of the array)

### 7. Combine with SORT:

```excel
=CHOOSEROWS(SORT(A1:D10, 2), 1, 2, 3)
```

**Result:**
```
Sorts data by column 2, then returns only the first 3 rows
```

### 8. Extract First and Last Rows:

```excel
=CHOOSEROWS(A1:D10, 1, -1)
```

**Result:**
```
Returns the first row and the last row
```

### 9. Reverse Row Order:

```excel
=CHOOSEROWS(A1:D5, 5, 4, 3, 2, 1)
```

**Result:**
```
Returns all rows in reverse order (bottom to top)
```

## Notes:

- `CHOOSEROWS` is available in Excel 365 and Excel 2021 or later versions.
- Row indices must be non-zero integers; 0 returns a `#VALUE!` error.
- If any row index exceeds the number of rows in the array, Excel returns a `#VALUE!` error.
- The function preserves all columns from the original array.
- Results automatically spill into adjacent cells.

## Applications:

- **Row Selection**: Extract only the rows you need from a large dataset.
- **Row Reordering**: Rearrange rows without modifying the source data.
- **Top/Bottom N**: Select specific rows like first, last, or middle entries.
- **Data Sampling**: Pick specific rows for analysis or reporting.
- **Row Duplication**: Repeat rows for formatting or calculation purposes.

## Related Functions:

- **CHOOSECOLS**: Returns specified columns from an array (column equivalent of CHOOSEROWS).
- **DROP**: Removes a specified number of rows or columns from an array.
- **TAKE**: Extracts a specified number of rows or columns from an array.
- **INDEX**: Returns a value or reference from a specific position in an array.
- **VSTACK**: Vertically combines arrays top to bottom.
- **FILTER**: Returns rows that meet specified criteria.

> **Tip:** Combine `CHOOSEROWS` with `CHOOSECOLS` to extract a specific subset of both rows and columns from a dataset. For example, `=CHOOSECOLS(CHOOSEROWS(data, 1, 2, 3), 1, 3)` returns columns 1 and 3 from the first three rows.