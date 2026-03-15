<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# FORMULATEXT Function

The `FORMULATEXT` function in Excel is used to **return the formula in a given cell as text**. It displays the actual formula rather than the calculated result, which is useful for documentation, auditing, or troubleshooting spreadsheets.

## Key Features of `FORMULATEXT`:

- Returns the **exact formula** as it appears in the formula bar.
- Shows formulas from other cells without having to navigate to them.
- Useful for **formula auditing** and creating documentation.
- Returns an error if the referenced cell doesn't contain a formula.

## Syntax:

```plaintext
FORMULATEXT(reference)
```

- **reference**: A reference to a cell that contains a formula you want to display as text.

## How `FORMULATEXT` Works:

1. Excel looks at the specified cell reference.
2. If the cell contains a formula, it returns that formula as a text string.
3. If the cell contains a value (not a formula), it returns a `#N/A` error.
4. The returned text includes the leading equals sign (=) and the complete formula.

## Examples:

### 1. Display a Simple Formula:

If cell `A1` contains the formula `=B1+C1`:

```excel
=FORMULATEXT(A1)
```

**Result:**
```
=B1+C1
```

### 2. Show Complex Formulas:

If cell `D5` contains `=VLOOKUP(A2,Table1,3,FALSE)`:

```excel
=FORMULATEXT(D5)
```

**Result:**
```
=VLOOKUP(A2,Table1,3,FALSE)
```

### 3. Error When No Formula Exists:

If cell `A1` contains the value `100` (not a formula):

```excel
=FORMULATEXT(A1)
```

**Result:**
```
#N/A
```

### 4. Create Formula Documentation:

```excel
=A1&" uses the formula: "&FORMULATEXT(A1)
```

If `A1` contains `=SUM(B1:B10)` and evaluates to `500`:

**Result:**
```
500 uses the formula: =SUM(B1:B10)
```

## Notes:

- `FORMULATEXT` returns a `#N/A` error if the referenced cell contains a value instead of a formula.
- The function is **available in Excel 2013 and later versions**.
- Returns the formula exactly as entered, including any spaces or formatting.
- Works with **array formulas** and will show the complete array syntax.
- Cannot reference cells from **closed workbooks**.

## Applications:

- **Formula Auditing**: Quickly view formulas in multiple cells without clicking on each one.
- **Documentation**: Create lists of formulas used in your workbook for reference.
- **Quality Control**: Check that formulas are consistent across similar calculations.
- **Training Materials**: Show both the formula and result in educational spreadsheets.
- **Troubleshooting**: Identify formula differences when debugging calculation errors.

## Error Handling:

You can combine `FORMULATEXT` with error handling to make it more robust:

```excel
=IFERROR(FORMULATEXT(A1), "No formula in this cell")
```

This will display the formula if one exists, or a custom message if the cell contains only a value.