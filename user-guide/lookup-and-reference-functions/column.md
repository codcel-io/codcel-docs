<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COLUMN Function

The `COLUMN` function in Excel is used to **return the column number of a cell reference**. When no reference is provided, it returns the column number of the cell containing the formula.

## Key Features of `COLUMN`:

- Returns the column number of a given cell reference.
- If no reference is provided, returns the column number of the cell where the formula is entered.
- Works with single cell references, ranges, and named ranges.
- When given a range, returns the column number of the first column in the range.
- Useful for creating dynamic formulas that adapt to column positions.

## Syntax:

```plaintext
COLUMN([reference])
```

- **reference** (optional): A cell or range of cells for which you want the column number. If omitted, returns the column number of the cell containing the formula.

## How `COLUMN` Works:

1. The function receives an optional reference as input.
2. If a reference is provided, it returns the column number of that reference.
3. If no reference is provided, it returns the column number of the cell containing the formula.
4. For ranges, it returns the column number of the leftmost column.

## Examples:

### 1. Get Column Number of a Specific Cell:

```excel
=COLUMN(C1)
```

**Result:**
```
3
```

### 2. Get Column Number Without Reference:

```excel
=COLUMN()
```

**Result:**
```
Returns the column number of the cell containing this formula
```

### 3. Get Column Number of a Range:

```excel
=COLUMN(D5:F10)
```

**Result:**
```
4
```
(Returns the column number of the first column in the range, which is D)

### 4. Use with INDIRECT for Dynamic Column Reference:

```excel
=COLUMN(INDIRECT("E1"))
```

**Result:**
```
5
```

### 5. Create Sequential Column Numbers Across a Row:

```excel
=COLUMN(A1)
```

**Result when copied across columns:**
```
1   2   3   4   5   ...
```

### 6. Combine with ROW for Cell Identification:

```excel
=ADDRESS(ROW(), COLUMN())
```

**Result:**
```
Returns the address of the current cell (e.g., "$A$1")
```

### 7. Use in Conditional Formatting Logic:

```excel
=MOD(COLUMN(), 2) = 0
```

**Result:**
```
Returns TRUE for even-numbered columns, FALSE for odd
```

### 8. Dynamic Column Selection with INDEX:

```excel
=INDEX(A1:E1, COLUMN(C1))
```

**Result:**
```
Returns the value in the 3rd position of A1:E1
```

### 9. Create Alternating Patterns:

```excel
=IF(MOD(COLUMN(), 2) = 1, "Odd", "Even")
```

**Result:**
```
Returns "Odd" for columns A, C, E, etc. and "Even" for B, D, F, etc.
```

### 10. Calculate Relative Column Position:

```excel
=COLUMN() - COLUMN($A$1) + 1
```

**Result:**
```
Returns the relative position from column A (1, 2, 3, ...)
```

## Notes:

- `COLUMN` is available in all versions of Excel.
- The function always returns a positive integer (minimum value is 1).
- Column A is 1, column B is 2, and so on.
- When used with an array formula, `COLUMN` can return an array of column numbers.
- If the reference argument is a range, only the column number of the first column is returned (not an array).
- `COLUMN` is often paired with `ROW` for cell position calculations.

## Applications:

- **Dynamic Formulas**: Create formulas that automatically adjust based on column position.
- **Alternating Formatting**: Build conditional formatting rules based on column numbers.
- **Array Formulas**: Generate column indices for use with INDEX, CHOOSE, or other functions.
- **Data Validation**: Create rules that depend on column position.
- **Report Building**: Calculate statistics or apply logic based on column location.
- **Navigation**: Determine the position of data within a range.

## Related Functions:

- **COLUMNS**: Returns the number of columns in a reference or array.
- **ROW**: Returns the row number of a reference.
- **ROWS**: Returns the number of rows in a reference or array.
- **ADDRESS**: Returns a cell address as text given row and column numbers.
- **INDIRECT**: Returns a reference specified by a text string.
- **INDEX**: Returns a value at a given position in a range or array.
- **MATCH**: Returns the relative position of a value in a range.

> **Tip:** Use `COLUMN` with `ROW` to create unique identifiers for each cell. For example, `=ROW() * 1000 + COLUMN()` creates a unique number for each cell based on its position.