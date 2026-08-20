<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# TOROW Function

The `TOROW` function in Excel is used to **convert an array or range into a single row**. It takes a multi-dimensional array and returns all values arranged in a single horizontal row. This is particularly useful for flattening data, preparing lists for other functions, or transforming tabular data into a row format.

## Key Features of `TOROW`:

- Converts any array or range into a single row.
- Allows control over the scan order (by row or by column).
- Can ignore blanks during conversion (see the note on `ignore` below — Codcel does not filter errors).
- Works seamlessly with other dynamic array functions.
- Returns a spilled array that resizes automatically.

## Syntax:

```plaintext
TOROW(array, [ignore], [scan_by_column])
```

- **array**: The array or range to convert to a single row.
- **ignore** (optional): Specifies what to ignore. Default is 0.
  - `0` - Keep all values (default)
  - `1` - Ignore blanks
  - `2` - Ignore errors in Excel. **Codcel does not filter errors — this behaves as `0`.**
  - `3` - Ignore blanks and errors in Excel. **Codcel filters blanks only, so this behaves as `1`.**
- **scan_by_column** (optional): Specifies how to read the array. Default is FALSE.
  - `FALSE` - Scan the array by row (left to right, then down). This is the default.
  - `TRUE` - Scan the array by column (top to bottom, then right).

## How `TOROW` Works:

1. Takes the input array and reads each value in the specified order.
2. By default, scans by row (left to right across each row, then moves to the next row).
3. If `scan_by_column` is TRUE, scans by column (top to bottom in each column, then moves to the next column).
4. Optionally filters out blanks based on the `ignore` parameter. Codcel does not filter error values.
5. Returns all values arranged into a single horizontal row.

## Examples:

### 1. Basic Conversion (Scan by Row):

Given a range A1:C2 with data:
```
1   2   3
4   5   6
```

```excel
=TOROW(A1:C2)
```

**Result:**
```
1   2   3   4   5   6
```

(Values are read left to right, row by row)

### 2. Scan by Column:

Using the same range A1:C2:

```excel
=TOROW(A1:C2, 0, TRUE)
```

**Result:**
```
1   4   2   5   3   6
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
=TOROW(A1:B3, 1)
```

**Result:**
```
A   B   C   D
```

(Blank cells are removed from the result)

### 4. Ignore Errors (Not Filtered in Codcel):

Given a range with errors:
```
1       2
#N/A    3
4       #VALUE!
```

```excel
=TOROW(A1:B3, 2)
```

**Result:**
```
All six values, errors included — Codcel does not filter errors, so `2` behaves as `0`
```

(In Excel this would exclude `#N/A` and `#VALUE!`. In Codcel the errors are retained and propagate to the
result. Filter them out with `IFERROR` before calling `TOROW` if you need Excel's behaviour.)

### 5. Ignore Both Blanks and Errors (Blanks Only in Codcel):

```excel
=TOROW(A1:C3, 3)
```

**Result:**
```
Returns non-blank values in a single row — error values are retained
```

(Codcel treats `3` the same as `1`. In Excel this would also drop error values.)

### 6. Convert Array Constant:

```excel
=TOROW({1,2,3;4,5,6;7,8,9})
```

**Result:**
```
1   2   3   4   5   6   7   8   9
```

### 7. Combine with UNIQUE:

```excel
=UNIQUE(TOROW(A1:C10))
```

**Result:**
```
Returns unique values from the entire range as a single row
```

### 8. Flatten for TEXTJOIN:

```excel
=TEXTJOIN(", ", TRUE, TOROW(A1:C3))
```

**Result:**
```
Joins all values from the range into a comma-separated string
```

## Notes:

- `TOROW` is available in Excel 365 and Excel 2021 or later versions.
- The function returns a dynamic spilled array.
- When `ignore` is set to filter values, the resulting array may be smaller than the original.
- **Codcel difference:** the `ignore` argument filters blanks only. `2` (ignore errors) is a no-op and `3`
  (ignore blanks and errors) drops blanks alone. An out-of-range `ignore` value is accepted silently and
  treated as `0` rather than returning `#VALUE!`. See
  [Known Function Differences](../differences/known-function-differences.md).
- If the input array is already a single row, `TOROW` returns it unchanged (unless filtering is applied).
- Empty results return a `#CALC!` error if all values are filtered out.

## Applications:

- **Data Flattening**: Convert multi-row data into a single list for analysis.
- **List Preparation**: Prepare data for functions that require single-row input.
- **Data Cleaning**: Remove blanks or errors while reshaping data.
- **Dynamic Reporting**: Combine data from multiple rows into a unified row format.
- **Array Manipulation**: Transform array shapes for use with other dynamic array functions.

## Related Functions:

- **TOCOL**: Converts an array to a single column (vertical equivalent of TOROW).
- **WRAPCOLS**: Wraps a row or column into multiple columns.
- **WRAPROWS**: Wraps a row or column into multiple rows.
- **VSTACK**: Vertically stacks arrays on top of each other.
- **HSTACK**: Horizontally stacks arrays side by side.

> **Tip:** Use `TOROW` combined with `UNIQUE` and `SORT` to quickly generate a sorted list of unique values from a multi-row range: `=SORT(UNIQUE(TOROW(A1:C10, 1)))`.