<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TOCOL Function

The `TOCOL` function in Excel is used to **convert an array or range into a single column**. It takes a multi-dimensional array and returns all values arranged in a single vertical column. This is particularly useful for flattening data, preparing lists for other functions, or transforming tabular data into a columnar format.

## Key Features of `TOCOL`:

- Converts any array or range into a single column.
- Allows control over the scan order (by row or by column).
- Can ignore blanks, errors, or both during conversion.
- Works seamlessly with other dynamic array functions.
- Returns a spilled array that resizes automatically.

## Syntax:

```plaintext
TOCOL(array, [ignore], [scan_by_column])
```

- **array**: The array or range to convert to a single column.
- **ignore** (optional): Specifies what to ignore. Default is 0.
  - `0` - Keep all values (default)
  - `1` - Ignore blanks
  - `2` - Ignore errors
  - `3` - Ignore blanks and errors
- **scan_by_column** (optional): Specifies how to read the array. Default is FALSE.
  - `FALSE` - Scan the array by row (left to right, then down). This is the default.
  - `TRUE` - Scan the array by column (top to bottom, then right).

## How `TOCOL` Works:

1. Takes the input array and reads each value in the specified order.
2. By default, scans by row (left to right across each row, then moves to the next row).
3. If `scan_by_column` is TRUE, scans by column (top to bottom in each column, then moves to the next column).
4. Optionally filters out blanks and/or errors based on the `ignore` parameter.
5. Returns all values stacked into a single vertical column.

## Examples:

### 1. Basic Conversion (Scan by Row):

Given a range A1:C2 with data:
```
1   2   3
4   5   6
```

```excel
=TOCOL(A1:C2)
```

**Result:**
```
1
2
3
4
5
6
```

(Values are read left to right, row by row)

### 2. Scan by Column:

Using the same range A1:C2:

```excel
=TOCOL(A1:C2, 0, TRUE)
```

**Result:**
```
1
4
2
5
3
6
```

(Values are read top to bottom, column by column)

### 3. Ignore Blanks:

Given a range with blanks:
```
A   B
    C
D
```

```excel
=TOCOL(A1:B3, 1)
```

**Result:**
```
A
B
C
D
```

(Blank cells are removed from the result)

### 4. Ignore Errors:

Given a range with errors:
```
1       2
#N/A    3
4       #VALUE!
```

```excel
=TOCOL(A1:B3, 2)
```

**Result:**
```
1
2
3
4
```

(Error values are excluded from the result)

### 5. Ignore Both Blanks and Errors:

```excel
=TOCOL(A1:C3, 3)
```

**Result:**
```
Returns only non-blank, non-error values in a single column
```

### 6. Convert Array Constant:

```excel
=TOCOL({1,2,3;4,5,6;7,8,9})
```

**Result:**
```
1
2
3
4
5
6
7
8
9
```

### 7. Combine with UNIQUE:

```excel
=UNIQUE(TOCOL(A1:C10))
```

**Result:**
```
Returns unique values from the entire range as a single column
```

### 8. Flatten for TEXTJOIN:

```excel
=TEXTJOIN(", ", TRUE, TOCOL(A1:C3))
```

**Result:**
```
Joins all values from the range into a comma-separated string
```

## Notes:

- `TOCOL` is available in Excel 365 and Excel 2021 or later versions.
- The function returns a dynamic spilled array.
- When `ignore` is set to filter values, the resulting array may be smaller than the original.
- If the input array is already a single column, `TOCOL` returns it unchanged (unless filtering is applied).
- Empty results return a `#CALC!` error if all values are filtered out.

## Applications:

- **Data Flattening**: Convert multi-column data into a single list for analysis.
- **List Preparation**: Prepare data for functions that require single-column input like UNIQUE, SORT, or FILTER.
- **Data Cleaning**: Remove blanks or errors while reshaping data.
- **Dynamic Reporting**: Combine data from multiple columns into a unified column format.
- **Array Manipulation**: Transform array shapes for use with other dynamic array functions.

## Related Functions:

- **TOROW**: Converts an array to a single row (horizontal equivalent of TOCOL).
- **WRAPCOLS**: Wraps a row or column into multiple columns.
- **WRAPROWS**: Wraps a row or column into multiple rows.
- **VSTACK**: Vertically stacks arrays on top of each other.
- **HSTACK**: Horizontally stacks arrays side by side.

> **Tip:** Use `TOCOL` combined with `UNIQUE` and `SORT` to quickly generate a sorted list of unique values from a multi-column range: `=SORT(UNIQUE(TOCOL(A1:C10, 1)))`.