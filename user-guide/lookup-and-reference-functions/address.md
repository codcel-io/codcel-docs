<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ADDRESS Function

The `ADDRESS` function in Excel is used to **create a cell address as a text string, given a row number and column number**. It constructs a cell reference in either A1-style or R1C1-style notation, with options for absolute or relative referencing and optional sheet name qualification.

## Key Features of `ADDRESS`:

- Builds a cell reference string from row and column numbers.
- Supports four reference types: fully absolute, mixed (two variants), and fully relative.
- Can produce A1-style (e.g., `$A$1`) or R1C1-style (e.g., `R1C1`) references.
- Optionally prepends a worksheet name for cross-sheet references.
- Returns a text string, not a live reference — use `INDIRECT` to convert it into an actual reference.

## Syntax:

```plaintext
ADDRESS(row_num, column_num, [abs_num], [a1], [sheet_text])
```

- **row_num**: The row number to use in the cell reference.
- **column_num**: The column number to use in the cell reference.
- **abs_num** (optional): The type of reference to return. Defaults to 1.
  - `1` — Absolute row and absolute column (e.g., `$A$1`)
  - `2` — Absolute row, relative column (e.g., `A$1`)
  - `3` — Relative row, absolute column (e.g., `$A1`)
  - `4` — Relative row and relative column (e.g., `A1`)
- **a1** (optional): A logical value specifying the reference style. Defaults to TRUE.
  - `TRUE` — A1-style reference (e.g., `$A$1`)
  - `FALSE` — R1C1-style reference (e.g., `R1C1`)
- **sheet_text** (optional): A text string specifying the worksheet name. When provided, the result is prefixed with the sheet name (e.g., `Sheet1!$A$1`).

## How `ADDRESS` Works:

1. Takes the given row number and column number.
2. Converts the column number to a letter (for A1-style) or keeps it as a number (for R1C1-style).
3. Applies the specified reference style (absolute, mixed, or relative) by adding or omitting `$` signs.
4. If a sheet name is provided, prepends it with an exclamation mark separator.
5. Returns the constructed cell address as a text string.

## Examples:

### 1. Basic Absolute Reference (Default):

```excel
=ADDRESS(1, 1)
```

**Result:**
```
$A$1
```

Explanation: Row 1, Column 1 with the default absolute reference style produces `$A$1`.

### 2. Fully Relative Reference:

```excel
=ADDRESS(3, 2, 4)
```

**Result:**
```
B3
```

Explanation: Row 3, Column 2 with `abs_num` = 4 (relative) produces `B3` without `$` signs.

### 3. Mixed References:

```excel
=ADDRESS(5, 3, 2)
```

**Result:**
```
C$5
```

Explanation: Row 5, Column 3 with `abs_num` = 2 (absolute row, relative column) produces `C$5`.

```excel
=ADDRESS(5, 3, 3)
```

**Result:**
```
$C5
```

Explanation: Row 5, Column 3 with `abs_num` = 3 (relative row, absolute column) produces `$C5`.

### 4. R1C1-Style Reference:

```excel
=ADDRESS(2, 4, 1, FALSE)
```

**Result:**
```
R2C4
```

Explanation: Row 2, Column 4 with R1C1-style (`a1` = FALSE) produces `R2C4`.

### 5. With Sheet Name:

```excel
=ADDRESS(1, 1, 1, TRUE, "Sales")
```

**Result:**
```
Sales!$A$1
```

Explanation: Produces an absolute reference to cell A1 on the "Sales" worksheet.

### 6. Sheet Name with Spaces:

```excel
=ADDRESS(3, 5, 1, TRUE, "Q1 Data")
```

**Result:**
```
'Q1 Data'!$E$3
```

Explanation: When the sheet name contains spaces, Excel wraps it in single quotes.

### 7. Combined with INDIRECT for Dynamic References:

```excel
=INDIRECT(ADDRESS(2, 3))
```

**Result:**
```
Returns the value in cell C2
```

Explanation: `ADDRESS(2, 3)` produces `$C$2`, then `INDIRECT` converts it into a live reference and returns the value in that cell.

### 8. Combined with ROW and COLUMN:

```excel
=ADDRESS(ROW(), COLUMN())
```

**Result:**
```
Returns the address of the cell containing the formula (e.g., $A$1 if placed in A1)
```

### 9. Building a Dynamic Range Reference:

```excel
=INDIRECT(ADDRESS(1, 1) & ":" & ADDRESS(10, 3))
```

**Result:**
```
Returns a reference to the range $A$1:$C$10
```

Explanation: Constructs a range reference string using two `ADDRESS` calls, then converts it with `INDIRECT`.

## Notes:

- `ADDRESS` returns a **text string**, not a cell reference. To use the result as an actual reference, wrap it in the `INDIRECT` function.
- If `row_num` or `column_num` is less than 1, `ADDRESS` returns a `#VALUE!` error.
- The column number is automatically converted to the corresponding letter(s) in A1-style. For example, column 27 becomes `AA`, column 702 becomes `ZZ`.
- When `sheet_text` contains special characters or spaces, Excel automatically encloses it in single quotes in the output.
- `ADDRESS` is often used in combination with `ROW`, `COLUMN`, `MATCH`, and `INDIRECT` to create dynamic cell references.
- In R1C1 mode with relative references (`abs_num` = 4), the output uses bracket notation like `R[2]C[4]`.

## Applications:

- **Dynamic Cell References**: Build cell references on the fly based on calculated row and column positions.
- **Cross-Sheet Formulas**: Construct references to cells on other worksheets dynamically.
- **Formula Auditing**: Generate cell addresses for documentation, logging, or error-checking purposes.
- **Dynamic Range Construction**: Combine with `INDIRECT` to create flexible range references that adapt to changing data layouts.
- **Data Validation**: Use in formulas that need to display or reference specific cell locations based on user input.

## Related Functions:

- **INDIRECT**: Converts a text string representing a cell reference into an actual reference.
- **ROW**: Returns the row number of a reference.
- **COLUMN**: Returns the column number of a reference.
- **OFFSET**: Returns a reference to a range offset from a starting cell.
- **MATCH**: Returns the relative position of an item in a range.
- **INDEX**: Returns a value or reference from a specific position in an array or range.

> **Tip:** Since `ADDRESS` returns text rather than a reference, pair it with `INDIRECT` when you need a live reference for calculations. For example, `=SUM(INDIRECT(ADDRESS(1,1) & ":" & ADDRESS(10,1)))` sums A1:A10 dynamically.