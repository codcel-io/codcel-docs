<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TRANSPOSE Function

The `TRANSPOSE` function in Excel is used to **rotate the orientation of a range or array**, converting rows to columns and columns to rows. This transforms a vertical range into a horizontal range, or vice versa.

## Key Features of `TRANSPOSE`:

- Converts rows to columns and columns to rows.
- Works with ranges, arrays, and array constants.
- Produces a dynamic array result in Excel 365 and Excel 2021.
- Useful for restructuring data layouts without manual copying.
- Can be combined with other array functions for complex data transformations.

## Syntax:

```plaintext
TRANSPOSE(array)
```

- **array**: The array or range to transpose. Rows become columns and columns become rows.

## How `TRANSPOSE` Works:

1. The function takes each row from the original array and converts it into a column.
2. Similarly, each column from the original array becomes a row.
3. The resulting array has dimensions swapped: an m×n array becomes an n×m array.
4. The original data remains unchanged; TRANSPOSE returns a new transposed array.
5. In legacy Excel versions, TRANSPOSE was entered as an array formula with Ctrl+Shift+Enter.

## Examples:

### 1. Transpose a Horizontal Range to Vertical:

```excel
=TRANSPOSE(A1:D1)
```

**Result:**
```
If A1:D1 contains: Apple  Banana  Cherry  Date

The result is a vertical column:
Apple
Banana
Cherry
Date
```

### 2. Transpose a Vertical Range to Horizontal:

```excel
=TRANSPOSE(A1:A4)
```

**Result:**
```
If A1:A4 contains:
Apple
Banana
Cherry
Date

The result is: Apple  Banana  Cherry  Date
```

### 3. Transpose a 2D Array:

```excel
=TRANSPOSE(A1:C3)
```

**Result:**
```
Original (3 rows × 3 columns):
1   2   3
4   5   6
7   8   9

Transposed (3 rows × 3 columns):
1   4   7
2   5   8
3   6   9
```

### 4. Transpose an Array Constant:

```excel
=TRANSPOSE({1,2,3;4,5,6})
```

**Result:**
```
Original (2 rows × 3 columns):
1   2   3
4   5   6

Transposed (3 rows × 2 columns):
1   4
2   5
3   6
```

### 5. Transpose a Single Row to a Column:

```excel
=TRANSPOSE({"Red","Green","Blue"})
```

**Result:**
```
Red
Green
Blue
```

### 6. Transpose a Single Column to a Row:

```excel
=TRANSPOSE({"Mon";"Tue";"Wed";"Thu";"Fri"})
```

**Result:**
```
Mon  Tue  Wed  Thu  Fri
```

### 7. Combine with SEQUENCE for Transposed Sequences:

```excel
=TRANSPOSE(SEQUENCE(1, 5))
```

**Result:**
```
Converts 1  2  3  4  5 (horizontal) to:
1
2
3
4
5
(vertical)
```

### 8. Use with Other Functions for Data Restructuring:

```excel
=TRANSPOSE(SORT(A1:D1, , , TRUE))
```

**Result:**
```
Sorts a horizontal range and transposes the result to vertical
```

## Notes:

- `TRANSPOSE` is available in all modern versions of Excel.
- In Excel 365 and Excel 2021, TRANSPOSE returns a dynamic array that spills automatically.
- In older Excel versions, you must select the output range, enter the formula, and press Ctrl+Shift+Enter.
- The output range dimensions must match the transposed dimensions (rows become columns and vice versa) in legacy mode.
- TRANSPOSE works with numbers, text, logical values, and error values.
- Empty cells in the source are preserved as empty cells in the transposed result.

## Applications:

- **Data Restructuring**: Convert row-based data to column-based or vice versa.
- **Report Formatting**: Reorient data for different presentation requirements.
- **Matrix Operations**: Prepare matrices for multiplication or other matrix functions.
- **Cross-tabulation**: Convert data between different tabular layouts.
- **Formula Compatibility**: Reshape arrays for use with functions that expect a specific orientation.

## Related Functions:

- **TOCOL**: Converts an array into a single column.
- **TOROW**: Converts an array into a single row.
- **HSTACK**: Horizontally combines arrays side by side.
- **VSTACK**: Vertically stacks arrays on top of each other.
- **CHOOSECOLS**: Returns specified columns from an array.
- **CHOOSEROWS**: Returns specified rows from an array.
- **WRAPROWS**: Wraps a row or column into a 2D array by rows.
- **WRAPCOLS**: Wraps a row or column into a 2D array by columns.

> **Tip:** Use `TRANSPOSE` with `SORT` or `FILTER` to reorient filtered or sorted data for different reporting layouts. This is particularly useful when preparing data for charts or pivot table-like summaries.