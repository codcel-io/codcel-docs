<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ISBLANK Function

The `ISBLANK` function in Excel is used to **check whether a cell is empty**. It returns TRUE if the referenced cell contains no data, and FALSE if the cell contains any value, including text, numbers, formulas, or errors. This function is useful for input validation, conditional logic, and handling missing data in spreadsheets.

## Key Features of `ISBLANK`:

- Returns `TRUE` if the cell is completely empty (no value, no formula).
- Returns `FALSE` if the cell contains any value, including zero, empty string (`""`), spaces, or an error.
- Works with cell references and ranges.
- Commonly used with `IF` to provide default values or trigger actions when data is missing.
- Does not treat zero (`0`) or empty strings (`""`) as blank — only truly empty cells return `TRUE`.

## Syntax:

```plaintext
ISBLANK(value)
```

- **value**: The cell reference or value you want to test for being blank. Typically a single cell reference such as `A1`.

## How `ISBLANK` Works:

1. `ISBLANK` examines the referenced cell to determine if it is completely empty.
2. If the cell has no content at all — no value, formula, or formatting artifact — it returns `TRUE`.
3. If the cell contains anything (a number, text, formula result, error, space character, or empty string), it returns `FALSE`.
4. When used with a literal value (e.g., `ISBLANK(0)`), it always returns `FALSE` because a value is being provided directly.

## Examples:

### 1. Empty Cell:

If A1 is completely empty:
```excel
=ISBLANK(A1)
```

**Result:**
```
TRUE
```

### 2. Cell Containing a Number:

If A1 contains `100`:
```excel
=ISBLANK(A1)
```

**Result:**
```
FALSE
```

### 3. Cell Containing Text:

If A1 contains `"Hello"`:
```excel
=ISBLANK(A1)
```

**Result:**
```
FALSE
```

### 4. Cell Containing Zero:

If A1 contains `0`:
```excel
=ISBLANK(A1)
```

**Result:**
```
FALSE
```

### 5. Cell with an Empty String Formula:

If A1 contains the formula `=""`:
```excel
=ISBLANK(A1)
```

**Result:**
```
FALSE (an empty string is not the same as a blank cell)
```

### 6. Conditional Default Value:

```excel
=IF(ISBLANK(A1), "No data", A1)
```

**Result:**
```
Returns "No data" if A1 is empty, otherwise returns the value in A1
```

### 7. Combined with AND for Multiple Checks:

```excel
=IF(AND(ISBLANK(A1), ISBLANK(B1)), "Both empty", "Has data")
```

**Result:**
```
Returns "Both empty" if both A1 and B1 are blank, otherwise "Has data"
```

### 8. Using with COUNTIF to Count Blank Cells:

```excel
=SUMPRODUCT(--ISBLANK(A1:A10))
```

**Result:**
```
Returns the number of blank cells in the range A1:A10
```

## Notes:

- A cell containing a formula that returns an empty string (`=""`) is NOT blank — `ISBLANK` returns `FALSE`.
- A cell containing only spaces is NOT blank — `ISBLANK` returns `FALSE`.
- `ISBLANK` only returns `TRUE` for cells that are genuinely empty (no content at all).
- When applied to a literal value (e.g., `ISBLANK(0)` or `ISBLANK("")`), it always returns `FALSE`.
- For checking if a cell's displayed value appears empty (including empty strings), consider using `LEN(TRIM(A1))=0` instead.
- `ISBLANK` is part of the IS family of information functions (`ISBLANK`, `ISERROR`, `ISNA`, `ISNUMBER`, `ISTEXT`, `ISLOGICAL`, etc.).

## Applications:

- **Input Validation**: Ensure required fields are filled in before processing data.
- **Default Values**: Use with `IF` to substitute default values when cells are left empty.
- **Data Cleaning**: Identify and flag missing data in datasets for review or correction.
- **Conditional Formatting**: Drive formula-based conditional formatting to highlight empty cells.
- **Error Prevention**: Guard against errors in formulas that would fail on empty inputs (e.g., division by zero).

## Related Functions:

- **ISOMITTED**: Checks whether an argument was omitted in a LAMBDA function (different from checking if a cell is blank).
- **ISNUMBER**: Returns TRUE if the value is a number.
- **ISTEXT**: Returns TRUE if the value is text.
- **ISERROR**: Returns TRUE if the value is any error.
- **ISNA**: Returns TRUE if the value is the #N/A error.
- **TYPE**: Returns a numeric code indicating the data type of a value.
- **IF**: Tests a condition and returns different values for TRUE or FALSE.
- **COUNTBLANK**: Counts the number of empty cells in a range.

> **Tip:** Use `ISBLANK` when you need to distinguish between truly empty cells and cells containing zero or empty strings. If you want to treat both blank cells and empty strings as "empty," use `LEN(TRIM(A1))=0` or `A1=""` instead. For counting blank cells in a range, `COUNTBLANK` is more efficient than `SUMPRODUCT(--ISBLANK(range))`.