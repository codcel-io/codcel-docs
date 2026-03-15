<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DROP Function

The `DROP` function in Excel is used to **exclude a specified number of rows or columns** from the beginning or end of an array or range. This function is the complement of TAKE, useful for removing header rows, trailing data, or creating subsets by exclusion.

## Key Features of `DROP`:

- Excludes rows from the beginning or end of an array.
- Excludes columns from the left or right of an array.
- Can exclude both rows and columns simultaneously.
- Positive values drop from the start; negative values drop from the end.
- Works seamlessly with other dynamic array functions.

## Syntax:

```plaintext
DROP(array, rows, [columns])
```

- **array**: The array or range from which to exclude rows and/or columns.
- **rows**: The number of rows to exclude. Positive values drop from the top; negative values drop from the bottom. Use 0 or omit to keep all rows.
- **columns** (optional): The number of columns to exclude. Positive values drop from the left; negative values drop from the right. If omitted, all columns are kept.

## How `DROP` Works:

1. If `rows` is positive, `DROP` removes rows from the beginning of the array.
2. If `rows` is negative, `DROP` removes rows from the end of the array.
3. If `columns` is positive, `DROP` removes columns from the left side of the array.
4. If `columns` is negative, `DROP` removes columns from the right side of the array.
5. If a value exceeds the array dimensions, all rows/columns are removed and an error is returned.

## Examples:

### 1. Remove First 2 Rows (e.g., Header Rows):

Given a range A1:C10 with data:
```excel
=DROP(A1:C10, 2)
```

**Result:**
```
Returns rows 3-10 with all columns from A1:C10
```

### 2. Remove Last 3 Rows:

```excel
=DROP(A1:C10, -3)
```

**Result:**
```
Returns rows 1-7 with all columns from A1:C10
```

### 3. Remove First Row and First Column:

```excel
=DROP(A1:D10, 1, 1)
```

**Result:**
```
Returns rows 2-10 and columns B-D from A1:D10
```

### 4. Remove Last 2 Rows and Last Column:

```excel
=DROP(A1:D10, -2, -1)
```

**Result:**
```
Returns rows 1-8 and columns A-C from A1:D10
```

### 5. Remove All Rows but Keep Only Columns (Remove First 2 Columns):

```excel
=DROP(A1:D10, , 2)
```

**Result:**
```
Returns all rows with only columns C-D (first 2 columns removed)
```

### 6. Combine with SORT to Remove Top N After Sorting:

```excel
=DROP(SORT(A1:B10, 2, -1), 3)
```

**Result:**
```
Sorts by column 2 in descending order and removes the top 3 rows
```

### 7. Drop from an Array Constant:

```excel
=DROP({1,2,3;4,5,6;7,8,9}, 1, 1)
```

**Result:**
```
5   6
8   9
```

(Returns the array with the first row and first column removed)

### 8. Remove Header Row from Imported Data:

```excel
=DROP(IMPORTEDDATA, 1)
```

**Result:**
```
Returns the data without the header row
```

## Notes:

- `DROP` is available in Excel 365 and Excel 2021 or later versions.
- If the absolute value of `rows` or `columns` equals or exceeds the array dimensions, Excel returns a `#CALC!` error because no data remains.
- Using 0 for `rows` or `columns` (or omitting them) keeps all rows or columns respectively.
- `DROP` returns a `#CALC!` error if the array is empty.
- This function pairs well with `TAKE`, which keeps rows/columns instead of removing them.

## Applications:

- **Header Removal**: Remove header rows from datasets before processing.
- **Data Trimming**: Exclude first or last records that may be incomplete.
- **Nested Array Operations**: Combine with TAKE to extract middle sections of data.
- **Report Formatting**: Remove summary rows or metadata from exports.
- **Dynamic Data Cleanup**: Automatically exclude unwanted portions of imported data.

## Related Functions:

- **TAKE**: Extracts a specified number of rows or columns from an array (opposite of DROP).
- **FILTER**: Returns rows that meet specified criteria.
- **SORT**: Sorts an array by specified columns.
- **INDEX**: Returns a value or reference from a specific position in an array.
- **CHOOSECOLS**: Returns specified columns from an array.
- **CHOOSEROWS**: Returns specified rows from an array.

> **Tip:** Combine `DROP` with `TAKE` to extract a middle section of data. For example, `=TAKE(DROP(data, 2), 5)` removes the first 2 rows and then takes the next 5 rows, effectively extracting rows 3-7 from the original data.