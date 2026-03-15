<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COLUMNS Function

The `COLUMNS` function in Excel is used to **return the number of columns in a reference or array**. It counts how many columns are contained within a given range, array constant, or cell reference.

## Key Features of `COLUMNS`:

- Returns the total number of columns in a range, array, or reference.
- Works with cell references, array constants, and dynamic arrays.
- Useful for creating dynamic formulas that adapt to changing data dimensions.
- Often paired with the `ROWS` function to determine array dimensions.
- Returns a single numeric value regardless of the array size.

## Syntax:

```plaintext
COLUMNS(array)
```

- **array**: A reference, array constant, or range for which you want the number of columns.

## How `COLUMNS` Works:

1. The function examines the provided array or reference.
2. It counts the total number of columns spanning the range.
3. It returns this count as a single integer value.
4. For array constants, it counts the elements in a single row (columns are separated by commas in array notation).

## Examples:

### 1. Count Columns in a Range:

```excel
=COLUMNS(A1:D1)
```

**Result:**
```
4
```

### 2. Count Columns in a Multi-Row Range:

```excel
=COLUMNS(A1:D5)
```

**Result:**
```
4
```

### 3. Count Columns in an Array Constant:

```excel
=COLUMNS({1,2,3,4,5})
```

**Result:**
```
5
```

### 4. Count Columns in a 2D Array Constant:

```excel
=COLUMNS({1,2,3;4,5,6;7,8,9})
```

**Result:**
```
3
```

### 5. Calculate Total Cell Count:

```excel
=ROWS(A1:D10) * COLUMNS(A1:D10)
```

**Result:**
```
40
```

### 6. Use with SEQUENCE to Create Dynamic Arrays:

```excel
=SEQUENCE(1, COLUMNS(A1:E1))
```

**Result:**
```
1   2   3   4   5
```

### 7. Reference a Single Cell:

```excel
=COLUMNS(A1)
```

**Result:**
```
1
```

### 8. Use with CHOOSECOLS for Dynamic Column Selection:

```excel
=CHOOSECOLS(A1:E5, SEQUENCE(1, COLUMNS(A1:E5)))
```

**Result:**
```
Returns all columns from A1:E5
```

### 9. Combine with INDEX for Last Column:

```excel
=INDEX(A1:E1, COLUMNS(A1:E1))
```

**Result:**
```
Returns the value in E1 (the last column of the range)
```

### 10. Dynamic Range Expansion Check:

```excel
=IF(COLUMNS(A1:D1)>3, "Wide range", "Narrow range")
```

**Result:**
```
Wide range
```

## Notes:

- `COLUMNS` is available in all versions of Excel.
- The function always returns a positive integer (minimum value is 1).
- When used with a single cell reference, it returns 1.
- The function ignores the content of cells; it only counts the column structure.
- Array constants use commas to separate columns and semicolons to separate rows.
- Works seamlessly with dynamic array functions like `FILTER`, `SORT`, and `UNIQUE`.

## Applications:

- **Dynamic Formulas**: Create formulas that automatically adjust to data range changes.
- **Array Dimension Checks**: Validate or determine the size of arrays before processing.
- **Last Column Access**: Use with `INDEX` to retrieve values from the last column of a range.
- **Loop Simulation**: Combine with `SEQUENCE` to iterate over column indices.
- **Data Validation**: Ensure arrays meet expected dimensional requirements.
- **Report Building**: Dynamically size output ranges based on input dimensions.

## Related Functions:

- **COLUMN**: Returns the column number of a reference.
- **ROW**: Returns the row number of a reference.
- **ROWS**: Returns the number of rows in a reference or array.
- **INDEX**: Returns a value at a specified row and column position in a range.
- **CHOOSECOLS**: Returns specified columns from an array.
- **CHOOSEROWS**: Returns specified rows from an array.
- **TAKE**: Extracts a specified number of rows or columns from an array.
- **DROP**: Excludes a specified number of rows or columns from an array.
- **SEQUENCE**: Generates a sequence of numbers in an array.

> **Tip:** Use `ROWS(array) * COLUMNS(array)` to calculate the total number of cells in a range. This is useful for validating data sizes or creating summary statistics about your data structure.