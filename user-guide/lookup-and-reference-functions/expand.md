<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# EXPAND Function

The `EXPAND` function in Excel is used to **expand an array to specified dimensions** by adding rows and/or columns. When an array is expanded, empty positions are filled with a specified pad value (or `#N/A` by default).

## Key Features of `EXPAND`:

- Expands an array to a larger number of rows and/or columns.
- Fills new positions with a customizable pad value.
- If no pad value is specified, new cells contain `#N/A`.
- Works seamlessly with other dynamic array functions.
- Useful for aligning arrays of different sizes for calculations.

## Syntax:

```plaintext
EXPAND(array, rows, [columns], [pad_with])
```

- **array**: The array or range to expand.
- **rows**: The number of rows in the expanded array. Must be greater than or equal to the current number of rows. Use `#N/A` or omit to keep the current row count.
- **columns** (optional): The number of columns in the expanded array. Must be greater than or equal to the current number of columns. If omitted, the current column count is kept.
- **pad_with** (optional): The value to fill in new cells. If omitted, `#N/A` is used.

## How `EXPAND` Works:

1. The function takes the original array and increases its dimensions to match the specified rows and columns.
2. The original data remains in the top-left portion of the expanded array.
3. New cells created by the expansion are filled with the `pad_with` value.
4. If `rows` or `columns` is less than the array's current dimensions, a `#VALUE!` error is returned.
5. If the array is already the specified size, it is returned unchanged.

## Examples:

### 1. Expand a 2x2 Array to 4x4 with Default Padding:

```excel
=EXPAND({1,2;3,4}, 4, 4)
```

**Result:**
```
1       2       #N/A    #N/A
3       4       #N/A    #N/A
#N/A    #N/A    #N/A    #N/A
#N/A    #N/A    #N/A    #N/A
```

### 2. Expand with a Custom Pad Value (Zero):

```excel
=EXPAND({1,2;3,4}, 4, 4, 0)
```

**Result:**
```
1   2   0   0
3   4   0   0
0   0   0   0
0   0   0   0
```

### 3. Expand Only Rows:

```excel
=EXPAND(A1:C2, 5, , 0)
```

**Result:**
```
Returns the original 2 rows from A1:C2, plus 3 additional rows filled with 0s
```

### 4. Expand Only Columns:

```excel
=EXPAND(A1:B4, , 5, "-")
```

**Result:**
```
Returns the original 2 columns from A1:B4, plus 3 additional columns filled with "-"
```

### 5. Expand a Single Cell to Create a Filled Array:

```excel
=EXPAND({1}, 3, 3, 0)
```

**Result:**
```
1   0   0
0   0   0
0   0   0
```

### 6. Combine with SEQUENCE for Padded Arrays:

```excel
=EXPAND(SEQUENCE(2, 2), 4, 4, 0)
```

**Result:**
```
1   2   0   0
3   4   0   0
0   0   0   0
0   0   0   0
```

### 7. Expand a Range to Match Another Array's Size:

```excel
=EXPAND(A1:B2, ROWS(D1:D5), COLUMNS(D1:F1), 0)
```

**Result:**
```
Expands A1:B2 to a 5x3 array, padding with zeros
```

### 8. Use with Text Padding:

```excel
=EXPAND({"Apple","Banana"}, 2, 4, "N/A")
```

**Result:**
```
Apple   Banana  N/A     N/A
N/A     N/A     N/A     N/A
```

## Notes:

- `EXPAND` is available in Excel 365 and Excel 2021 or later versions.
- If `rows` is less than the array's row count or `columns` is less than the column count, Excel returns a `#VALUE!` error.
- Using `#N/A` for `rows` or `columns` keeps the original dimension unchanged.
- The `pad_with` value can be a number, text, logical value, or error value.
- `EXPAND` does not modify the original data; it creates a new expanded array.

## Applications:

- **Array Alignment**: Match array sizes before performing element-wise operations.
- **Data Padding**: Fill sparse data with default values for calculations.
- **Matrix Operations**: Create uniformly sized matrices for mathematical operations.
- **Report Formatting**: Ensure consistent table dimensions in dynamic reports.
- **Combining Data**: Prepare arrays of different sizes for HSTACK or VSTACK operations.

## Related Functions:

- **DROP**: Excludes a specified number of rows or columns from an array.
- **TAKE**: Extracts a specified number of rows or columns from an array.
- **HSTACK**: Horizontally combines arrays side by side.
- **VSTACK**: Vertically stacks arrays on top of each other.
- **CHOOSECOLS**: Returns specified columns from an array.
- **CHOOSEROWS**: Returns specified rows from an array.
- **WRAPCOLS**: Wraps a row or column into a 2D array by columns.
- **WRAPROWS**: Wraps a row or column into a 2D array by rows.

> **Tip:** Use `EXPAND` with a pad value of 0 when preparing arrays for mathematical operations like `MMULT`, where consistent dimensions are required. This ensures all arrays align properly without introducing `#N/A` errors in calculations.