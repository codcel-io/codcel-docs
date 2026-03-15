<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ROWS Function

The `ROWS` function in Excel is used to **return the number of rows in a reference or array**. It counts the total number of rows regardless of content, including empty cells.

## Key Features of `ROWS`:

- Returns the count of rows in a range, array, or reference.
- Works with cell references, named ranges, and array constants.
- Counts all rows including those with empty cells.
- Useful for dynamic formulas that need to know the size of a data range.
- Often used with other functions like INDEX, INDIRECT, and OFFSET.

## Syntax:

```plaintext
ROWS(array)
```

- **array**: A reference, array constant, or range for which you want the number of rows.

## How `ROWS` Works:

1. The function receives a reference or array as input.
2. It counts the total number of rows in the specified range or array.
3. Returns a single number representing the row count.
4. Empty cells within the range are still counted as part of a row.

## Examples:

### 1. Count Rows in a Range:

```excel
=ROWS(A1:A10)
```

**Result:**
```
10
```

### 2. Count Rows in a Multi-Column Range:

```excel
=ROWS(A1:D5)
```

**Result:**
```
5
```

### 3. Count Rows in an Array Constant:

```excel
=ROWS({1,2,3;4,5,6;7,8,9})
```

**Result:**
```
3
```

### 4. Use with Named Range:

```excel
=ROWS(SalesData)
```

**Result:**
```
Returns the number of rows in the named range "SalesData"
```

### 5. Combine with COLUMNS for Array Dimensions:

```excel
=ROWS(A1:D10) & " x " & COLUMNS(A1:D10)
```

**Result:**
```
10 x 4
```

### 6. Dynamic Last Row Calculation:

```excel
=INDEX(A:A, ROWS(A1:A100))
```

**Result:**
```
Returns the value in row 100 of column A
```

### 7. Use with SEQUENCE to Create Row Numbers:

```excel
=SEQUENCE(ROWS(A1:A10))
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
10
```

### 8. Calculate Average per Row:

```excel
=SUM(A1:D10)/ROWS(A1:D10)
```

**Result:**
```
Returns the average sum per row across the range
```

## Notes:

- `ROWS` is available in all versions of Excel.
- The function returns a single numeric value, not an array.
- If the array argument is a reference to a closed workbook, `ROWS` returns a `#REF!` error.
- For array constants, use semicolons (`;`) to separate rows and commas (`,`) to separate columns.
- `ROWS` counts the physical rows in the reference, not the number of non-empty rows.

## Applications:

- **Dynamic Formulas**: Create formulas that automatically adjust based on data range size.
- **Data Validation**: Verify that imported data has the expected number of rows.
- **Loop Alternatives**: Use with other functions to process data without VBA loops.
- **Report Building**: Calculate statistics like averages per row or total row counts.
- **Array Sizing**: Determine dimensions of arrays for use with other dynamic array functions.

## Related Functions:

- **COLUMN**: Returns the column number of a reference.
- **COLUMNS**: Returns the number of columns in a reference or array.
- **ROW**: Returns the row number of a reference.
- **COUNTA**: Counts non-empty cells in a range.
- **COUNT**: Counts cells containing numbers in a range.
- **INDEX**: Returns a value at a given position in a range or array.
- **OFFSET**: Returns a reference offset from a starting point.
- **INDIRECT**: Returns a reference specified by a text string.
- **CHOOSEROWS**: Returns specified rows from an array.

> **Tip:** Combine `ROWS` with `COLUMNS` to get the full dimensions of a range. For example, `=ROWS(A1:D10) * COLUMNS(A1:D10)` returns the total number of cells (40) in the range.