<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# CHOOSECOLS Function

The `CHOOSECOLS` function in Excel is used to **return specified columns from an array or range**. It allows you to select one or more columns by their index numbers and returns them in the order specified. This is particularly useful for rearranging column order, extracting specific columns, or duplicating columns within a dataset.

## Key Features of `CHOOSECOLS`:

- Extracts specific columns from an array or range by index.
- Returns columns in any order you specify.
- Supports negative indices to count from the right.
- Can duplicate columns by specifying the same index multiple times.
- Works seamlessly with other dynamic array functions.

## Syntax:

```plaintext
CHOOSECOLS(array, col_num1, [col_num2], …)
```

- **array**: The array or range from which to return columns.
- **col_num1**: The index of the first column to return. Use positive numbers to count from the left (1 = first column) or negative numbers to count from the right (-1 = last column).
- **col_num2, …** (optional): Additional column indices to return.

## How `CHOOSECOLS` Works:

1. Takes the input array and identifies the columns at each specified index.
2. Positive indices count from the left (1 is the first column).
3. Negative indices count from the right (-1 is the last column).
4. Returns the selected columns in the order specified.
5. If an index is out of range, Excel returns a `#VALUE!` error.

## Examples:

### 1. Extract a Single Column:

Given a range A1:D5 with data:
```excel
=CHOOSECOLS(A1:D5, 2)
```

**Result:**
```
Returns only the second column (column B) from the range
```

### 2. Extract Multiple Columns:

```excel
=CHOOSECOLS(A1:D5, 1, 3)
```

**Result:**
```
Returns the first and third columns (A and C) from the range
```

### 3. Reorder Columns:

```excel
=CHOOSECOLS(A1:D5, 4, 2, 1, 3)
```

**Result:**
```
Returns columns in order: D, B, A, C (reversed and rearranged)
```

### 4. Use Negative Indices:

```excel
=CHOOSECOLS(A1:D5, -1, -2)
```

**Result:**
```
Returns the last column and second-to-last column (D and C)
```

### 5. Duplicate a Column:

```excel
=CHOOSECOLS(A1:C5, 1, 2, 2, 3)
```

**Result:**
```
Returns columns A, B, B, C (column B appears twice)
```

### 6. Extract from an Array Constant:

```excel
=CHOOSECOLS({1,2,3;4,5,6;7,8,9}, 1, 3)
```

**Result:**
```
1   3
4   6
7   9
```

(Returns the first and third columns of the array)

### 7. Combine with SORT:

```excel
=CHOOSECOLS(SORT(A1:D10, 2), 1, 3)
```

**Result:**
```
Sorts data by column 2, then returns only columns 1 and 3
```

### 8. Extract First and Last Columns:

```excel
=CHOOSECOLS(A1:E10, 1, -1)
```

**Result:**
```
Returns the first column (A) and the last column (E)
```

## Notes:

- `CHOOSECOLS` is available in Excel 365 and Excel 2021 or later versions.
- Column indices must be non-zero integers; 0 returns a `#VALUE!` error.
- If any column index exceeds the number of columns in the array, Excel returns a `#VALUE!` error.
- The function preserves all rows from the original array.
- Results automatically spill into adjacent cells.

## Applications:

- **Column Selection**: Extract only the columns you need from a large dataset.
- **Column Reordering**: Rearrange columns without modifying the source data.
- **Report Building**: Create custom views by selecting specific columns.
- **Data Transformation**: Combine with SORT, FILTER, or other functions for complex queries.
- **Column Duplication**: Repeat columns for formatting or calculation purposes.

## Related Functions:

- **CHOOSEROWS**: Returns specified rows from an array (row equivalent of CHOOSECOLS).
- **DROP**: Removes a specified number of rows or columns from an array.
- **TAKE**: Extracts a specified number of rows or columns from an array.
- **INDEX**: Returns a value or reference from a specific position in an array.
- **HSTACK**: Horizontally combines arrays side by side.

> **Tip:** Combine `CHOOSECOLS` with `CHOOSEROWS` to extract a specific subset of both rows and columns from a dataset. For example, `=CHOOSEROWS(CHOOSECOLS(data, 1, 3), 1, 2, 3)` returns the first three rows of columns 1 and 3.