<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TAKE Function

The `TAKE` function in Excel is used to **extract a specified number of rows or columns** from the beginning or end of an array or range. This function is useful for retrieving the first or last records from a dataset, creating subsets of data, or working with dynamic arrays.

## Key Features of `TAKE`:

- Extracts rows from the beginning or end of an array.
- Extracts columns from the left or right of an array.
- Can extract both rows and columns simultaneously.
- Positive values extract from the start; negative values extract from the end.
- Works seamlessly with other dynamic array functions.

## Syntax:

```plaintext
TAKE(array, rows, [columns])
```

- **array**: The array or range from which to extract rows and/or columns.
- **rows**: The number of rows to extract. Positive values take from the top; negative values take from the bottom. Use 0 or omit to include all rows.
- **columns** (optional): The number of columns to extract. Positive values take from the left; negative values take from the right. If omitted, all columns are returned.

## How `TAKE` Works:

1. If `rows` is positive, `TAKE` returns rows from the beginning of the array.
2. If `rows` is negative, `TAKE` returns rows from the end of the array.
3. If `columns` is positive, `TAKE` returns columns from the left side of the array.
4. If `columns` is negative, `TAKE` returns columns from the right side of the array.
5. If a value exceeds the array dimensions, all available rows/columns are returned.

## Examples:

### 1. Extract First 3 Rows:

Given a range A1:C10 with data:
```excel
=TAKE(A1:C10, 3)
```

**Result:**
```
Returns the first 3 rows with all columns from A1:C10
```

### 2. Extract Last 2 Rows:

```excel
=TAKE(A1:C10, -2)
```

**Result:**
```
Returns the last 2 rows with all columns from A1:C10
```

### 3. Extract First 5 Rows and First 2 Columns:

```excel
=TAKE(A1:D10, 5, 2)
```

**Result:**
```
Returns the first 5 rows and first 2 columns from A1:D10
```

### 4. Extract Last 3 Rows and Last Column:

```excel
=TAKE(A1:D10, -3, -1)
```

**Result:**
```
Returns the last 3 rows and last column from A1:D10
```

### 5. Extract All Rows but Only First 2 Columns:

```excel
=TAKE(A1:D10, , 2)
```

**Result:**
```
Returns all rows with only the first 2 columns
```

### 6. Combine with SORT to Get Top N Values:

```excel
=TAKE(SORT(A1:B10, 2, -1), 5)
```

**Result:**
```
Sorts by column 2 in descending order and returns the top 5 rows
```

### 7. Extract from an Array Constant:

```excel
=TAKE({1,2,3;4,5,6;7,8,9}, 2, 2)
```

**Result:**
```
1   2
4   5
```

(Returns the first 2 rows and first 2 columns of the array)

## Notes:

- `TAKE` is available in Excel 365 and Excel 2021 or later versions.
- If the absolute value of `rows` or `columns` exceeds the array dimensions, Excel returns all available rows/columns without error.
- Using 0 for `rows` or `columns` (or omitting them) includes all rows or columns respectively.
- `TAKE` returns a `#CALC!` error if the array is empty.
- This function pairs well with `DROP`, which removes rows/columns instead of keeping them.

## Applications:

- **Top/Bottom N Analysis**: Extract the first or last N records from a sorted dataset.
- **Data Pagination**: Display specific portions of large datasets.
- **Report Summaries**: Extract header rows or the most recent entries.
- **Dynamic Dashboards**: Create live subsets that update automatically.
- **Preview Data**: Show a quick glimpse of large datasets.

## Related Functions:

- **DROP**: Removes a specified number of rows or columns from an array (opposite of TAKE).
- **FILTER**: Returns rows that meet specified criteria.
- **SORT**: Sorts an array by specified columns.
- **INDEX**: Returns a value or reference from a specific position in an array.
- **CHOOSECOLS**: Returns specified columns from an array.
- **CHOOSEROWS**: Returns specified rows from an array.

> **Tip:** Combine `TAKE` with `SORT` to easily extract the top or bottom N items from a dataset based on any column. For example, `=TAKE(SORT(data, 3, -1), 10)` returns the top 10 items sorted by column 3 in descending order.