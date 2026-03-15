<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# WRAPCOLS Function

The `WRAPCOLS` function in Excel is used to **wrap a row or column of values into a two-dimensional array by columns**. It takes a one-dimensional array and reshapes it into multiple columns of a specified size.

## Key Features of `WRAPCOLS`:

- Wraps a single row or column into a 2D array filled column by column.
- Allows you to specify how many values appear in each column.
- Fills any remaining cells with a customizable pad value (or `#N/A` by default).
- Works seamlessly with other dynamic array functions.
- Useful for reshaping data for reports, dashboards, and matrix operations.

## Syntax:

```plaintext
WRAPCOLS(vector, wrap_count, [pad_with])
```

- **vector**: A row or column of values to wrap.
- **wrap_count**: The maximum number of values per column (determines the number of rows in the result).
- **pad_with** (optional): The value to fill in empty cells if the vector doesn't divide evenly. If omitted, `#N/A` is used.

## How `WRAPCOLS` Works:

1. The function takes the source vector and reads its values sequentially.
2. It fills the first column with the first `wrap_count` values.
3. It then moves to the next column and continues filling until all values are placed.
4. If the total number of values is not evenly divisible by `wrap_count`, the remaining cells in the last column are filled with the `pad_with` value.
5. The result is a 2D array with `wrap_count` rows and as many columns as needed.

## Examples:

### 1. Wrap a Row into 3-Row Columns:

```excel
=WRAPCOLS({1,2,3,4,5,6,7,8,9}, 3)
```

**Result:**
```
1   4   7
2   5   8
3   6   9
```

### 2. Wrap with Padding (Uneven Division):

```excel
=WRAPCOLS({1,2,3,4,5,6,7,8}, 3)
```

**Result:**
```
1   4   7
2   5   8
3   6   #N/A
```

### 3. Wrap with Custom Pad Value:

```excel
=WRAPCOLS({1,2,3,4,5,6,7,8}, 3, 0)
```

**Result:**
```
1   4   7
2   5   8
3   6   0
```

### 4. Wrap a Column Range:

```excel
=WRAPCOLS(A1:A12, 4)
```

**Result:**
```
A1   A5   A9
A2   A6   A10
A3   A7   A11
A4   A8   A12
```

### 5. Wrap with Text Padding:

```excel
=WRAPCOLS({"Apple","Banana","Cherry","Date","Elderberry"}, 2, "-")
```

**Result:**
```
Apple       Cherry      Elderberry
Banana      Date        -
```

### 6. Combine with SEQUENCE:

```excel
=WRAPCOLS(SEQUENCE(1, 10), 5)
```

**Result:**
```
1   6
2   7
3   8
4   9
5   10
```

### 7. Wrap a Filtered List:

```excel
=WRAPCOLS(FILTER(A1:A20, B1:B20="Active"), 5, "")
```

**Result:**
```
Returns active items wrapped into 5-row columns, padding empty cells with blank text
```

### 8. Create a Calendar-Style Layout:

```excel
=WRAPCOLS(SEQUENCE(1, 28), 7, "")
```

**Result:**
```
1   8   15  22
2   9   16  23
3   10  17  24
4   11  18  25
5   12  19  26
6   13  20  27
7   14  21  28
```

## Notes:

- `WRAPCOLS` is available in Excel 365 and Excel 2021 or later versions.
- The `vector` must be a single row or single column; multi-row, multi-column arrays return a `#VALUE!` error.
- If `wrap_count` is less than 1 or not a valid number, Excel returns a `#VALUE!` error.
- The `pad_with` value can be a number, text, logical value, or error value.
- `WRAPCOLS` fills by column (top to bottom, then left to right), while `WRAPROWS` fills by row.

## Applications:

- **Data Reshaping**: Convert a long list into a multi-column layout for easier viewing.
- **Report Formatting**: Arrange data into fixed-height columns for dashboard displays.
- **Calendar Creation**: Wrap sequential dates or numbers into week-based columns.
- **Matrix Operations**: Prepare vectors for matrix calculations requiring specific dimensions.
- **Data Entry Forms**: Transform linear input into structured grid layouts.

## Related Functions:

- **WRAPROWS**: Wraps a row or column into a 2D array by rows (fills left to right, then top to bottom).
- **TOCOL**: Converts an array to a single column.
- **TOROW**: Converts an array to a single row.
- **TRANSPOSE**: Rotates rows to columns and columns to rows.
- **TAKE**: Extracts a specified number of rows or columns from an array.
- **DROP**: Excludes a specified number of rows or columns from an array.
- **CHOOSECOLS**: Returns specified columns from an array.
- **CHOOSEROWS**: Returns specified rows from an array.

> **Tip:** Use `WRAPCOLS` with `SEQUENCE` to quickly create grid layouts from sequential data. For example, `=WRAPCOLS(SEQUENCE(1,100),10)` creates a 10-row by 10-column grid of numbers 1 to 100 filled by columns.