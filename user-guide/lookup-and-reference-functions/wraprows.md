<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# WRAPROWS Function

The `WRAPROWS` function in Excel is used to **wrap a row or column of values into a two-dimensional array by rows**. It takes a one-dimensional array and reshapes it into multiple rows of a specified size.

## Key Features of `WRAPROWS`:

- Wraps a single row or column into a 2D array filled row by row.
- Allows you to specify how many values appear in each row.
- Fills any remaining cells with a customizable pad value (or `#N/A` by default).
- Works seamlessly with other dynamic array functions.
- Useful for reshaping data for reports, dashboards, and matrix operations.

## Syntax:

```plaintext
WRAPROWS(vector, wrap_count, [pad_with])
```

- **vector**: A row or column of values to wrap.
- **wrap_count**: The maximum number of values per row (determines the number of columns in the result).
- **pad_with** (optional): The value to fill in empty cells if the vector doesn't divide evenly. If omitted, `#N/A` is used.

## How `WRAPROWS` Works:

1. The function takes the source vector and reads its values sequentially.
2. It fills the first row with the first `wrap_count` values.
3. It then moves to the next row and continues filling until all values are placed.
4. If the total number of values is not evenly divisible by `wrap_count`, the remaining cells in the last row are filled with the `pad_with` value.
5. The result is a 2D array with `wrap_count` columns and as many rows as needed.

## Examples:

### 1. Wrap a Row into 3-Column Rows:

```excel
=WRAPROWS({1,2,3,4,5,6,7,8,9}, 3)
```

**Result:**
```
1   2   3
4   5   6
7   8   9
```

### 2. Wrap with Padding (Uneven Division):

```excel
=WRAPROWS({1,2,3,4,5,6,7,8}, 3)
```

**Result:**
```
1   2   3
4   5   6
7   8   #N/A
```

### 3. Wrap with Custom Pad Value:

```excel
=WRAPROWS({1,2,3,4,5,6,7,8}, 3, 0)
```

**Result:**
```
1   2   3
4   5   6
7   8   0
```

### 4. Wrap a Column Range:

```excel
=WRAPROWS(A1:A12, 4)
```

**Result:**
```
A1   A2   A3   A4
A5   A6   A7   A8
A9   A10  A11  A12
```

### 5. Wrap with Text Padding:

```excel
=WRAPROWS({"Apple","Banana","Cherry","Date","Elderberry"}, 2, "-")
```

**Result:**
```
Apple       Banana
Cherry      Date
Elderberry  -
```

### 6. Combine with SEQUENCE:

```excel
=WRAPROWS(SEQUENCE(1, 10), 5)
```

**Result:**
```
1   2   3   4   5
6   7   8   9   10
```

### 7. Wrap a Filtered List:

```excel
=WRAPROWS(FILTER(A1:A20, B1:B20="Active"), 5, "")
```

**Result:**
```
Returns active items wrapped into 5-column rows, padding empty cells with blank text
```

### 8. Create a Calendar-Style Layout:

```excel
=WRAPROWS(SEQUENCE(1, 28), 7, "")
```

**Result:**
```
1   2   3   4   5   6   7
8   9   10  11  12  13  14
15  16  17  18  19  20  21
22  23  24  25  26  27  28
```

## Notes:

- `WRAPROWS` is available in Excel 365 and Excel 2021 or later versions.
- The `vector` must be a single row or single column; multi-row, multi-column arrays return a `#VALUE!` error.
- If `wrap_count` is less than 1 or not a valid number, Excel returns a `#VALUE!` error.
- The `pad_with` value can be a number, text, logical value, or error value.
- `WRAPROWS` fills by row (left to right, then top to bottom), while `WRAPCOLS` fills by column.

## Applications:

- **Data Reshaping**: Convert a long list into a multi-row layout for easier viewing.
- **Report Formatting**: Arrange data into fixed-width rows for dashboard displays.
- **Calendar Creation**: Wrap sequential dates or numbers into week-based rows.
- **Matrix Operations**: Prepare vectors for matrix calculations requiring specific dimensions.
- **Data Entry Forms**: Transform linear input into structured grid layouts.

## Related Functions:

- **WRAPCOLS**: Wraps a row or column into a 2D array by columns (fills top to bottom, then left to right).
- **TOCOL**: Converts an array to a single column.
- **TOROW**: Converts an array to a single row.
- **TRANSPOSE**: Rotates rows to columns and columns to rows.
- **TAKE**: Extracts a specified number of rows or columns from an array.
- **DROP**: Excludes a specified number of rows or columns from an array.
- **CHOOSECOLS**: Returns specified columns from an array.
- **CHOOSEROWS**: Returns specified rows from an array.

> **Tip:** Use `WRAPROWS` with `SEQUENCE` to quickly create grid layouts from sequential data. For example, `=WRAPROWS(SEQUENCE(1,100),10)` creates a 10-row by 10-column grid of numbers 1 to 100 filled by rows.