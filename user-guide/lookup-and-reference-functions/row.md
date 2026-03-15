<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ROW Function

The `ROW` function in Excel is used to **return the row number of a cell reference**. When no reference is provided, it returns the row number of the cell containing the formula.

## Key Features of `ROW`:

- Returns the row number of a given cell reference.
- If no reference is provided, returns the row number of the cell where the formula is entered.
- Works with single cell references, ranges, and named ranges.
- When given a range, returns the row number of the first row in the range.
- Useful for creating dynamic formulas that adapt to row positions.

## Syntax:

```plaintext
ROW([reference])
```

- **reference** (optional): A cell or range of cells for which you want the row number. If omitted, returns the row number of the cell containing the formula.

## How `ROW` Works:

1. The function receives an optional reference as input.
2. If a reference is provided, it returns the row number of that reference.
3. If no reference is provided, it returns the row number of the cell containing the formula.
4. For ranges, it returns the row number of the topmost row.

## Examples:

### 1. Get Row Number of a Specific Cell:

```excel
=ROW(A5)
```

**Result:**
```
5
```

### 2. Get Row Number Without Reference:

```excel
=ROW()
```

**Result:**
```
Returns the row number of the cell containing this formula
```

### 3. Get Row Number of a Range:

```excel
=ROW(B10:D15)
```

**Result:**
```
10
```
(Returns the row number of the first row in the range, which is row 10)

### 4. Use with INDIRECT for Dynamic Row Reference:

```excel
=ROW(INDIRECT("A25"))
```

**Result:**
```
25
```

### 5. Create Sequential Row Numbers Down a Column:

```excel
=ROW(A1)
```

**Result when copied down rows:**
```
1
2
3
4
5
...
```

### 6. Combine with COLUMN for Cell Identification:

```excel
=ADDRESS(ROW(), COLUMN())
```

**Result:**
```
Returns the address of the current cell (e.g., "$A$1")
```

### 7. Use in Conditional Formatting Logic:

```excel
=MOD(ROW(), 2) = 0
```

**Result:**
```
Returns TRUE for even-numbered rows, FALSE for odd
```

### 8. Dynamic Row Selection with INDEX:

```excel
=INDEX(A1:A10, ROW(A3))
```

**Result:**
```
Returns the value in the 3rd position of A1:A10
```

### 9. Create Alternating Patterns:

```excel
=IF(MOD(ROW(), 2) = 1, "Odd", "Even")
```

**Result:**
```
Returns "Odd" for rows 1, 3, 5, etc. and "Even" for rows 2, 4, 6, etc.
```

### 10. Calculate Relative Row Position:

```excel
=ROW() - ROW($A$1) + 1
```

**Result:**
```
Returns the relative position from row 1 (1, 2, 3, ...)
```

## Notes:

- `ROW` is available in all versions of Excel.
- The function always returns a positive integer (minimum value is 1).
- Row 1 is the first row, row 2 is the second, and so on.
- When used with an array formula, `ROW` can return an array of row numbers.
- If the reference argument is a range, only the row number of the first row is returned (not an array).
- `ROW` is often paired with `COLUMN` for cell position calculations.

## Applications:

- **Dynamic Formulas**: Create formulas that automatically adjust based on row position.
- **Alternating Formatting**: Build conditional formatting rules based on row numbers.
- **Array Formulas**: Generate row indices for use with INDEX, CHOOSE, or other functions.
- **Data Validation**: Create rules that depend on row position.
- **Report Building**: Calculate statistics or apply logic based on row location.
- **Navigation**: Determine the position of data within a range.

## Related Functions:

- **ROWS**: Returns the number of rows in a reference or array.
- **COLUMN**: Returns the column number of a reference.
- **COLUMNS**: Returns the number of columns in a reference or array.
- **ADDRESS**: Returns a cell address as text given row and column numbers.
- **INDIRECT**: Returns a reference specified by a text string.
- **INDEX**: Returns a value at a given position in a range or array.
- **MATCH**: Returns the relative position of a value in a range.

> **Tip:** Use `ROW` with `COLUMN` to create unique identifiers for each cell. For example, `=ROW() * 1000 + COLUMN()` creates a unique number for each cell based on its position.