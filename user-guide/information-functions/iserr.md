<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ISERR Function

The `ISERR` function in Excel is used to **check whether a value is any error except #N/A**. It returns TRUE if the value is an error such as #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, or #NULL!, and FALSE for all non-error values and for the #N/A error. This function is useful when you want to handle errors in formulas while still allowing #N/A to propagate for separate handling with `ISNA` or `IFNA`.

## Key Features of `ISERR`:

- Returns `TRUE` for any error value **except** `#N/A`.
- Returns `FALSE` for non-error values (numbers, text, logicals, blanks) and for the `#N/A` error.
- Detects `#VALUE!`, `#REF!`, `#DIV/0!`, `#NUM!`, `#NAME?`, and `#NULL!` errors.
- Commonly used with `IF` to substitute default values or trigger actions when formula errors occur.
- Differs from `ISERROR`, which returns `TRUE` for **all** errors including `#N/A`.
- Allows `#N/A` errors from failed lookups to be handled separately, preserving the distinction between "not found" and other formula errors.

## Syntax:

```plaintext
ISERR(value)
```

- **value**: The value or expression you want to test for an error. Typically a cell reference or formula result.

## How `ISERR` Works:

1. `ISERR` evaluates the provided value or expression.
2. If the result is an error value other than `#N/A` — such as `#VALUE!`, `#REF!`, `#DIV/0!`, `#NUM!`, `#NAME?`, or `#NULL!` — it returns `TRUE`.
3. If the result is `#N/A`, it returns `FALSE` (unlike `ISERROR`, which would return `TRUE`).
4. If the result is any non-error value (number, text, logical, blank), it returns `FALSE`.

## Examples:

### 1. Division by Zero Error:

If A1 contains a formula that results in `#DIV/0!`:
```excel
=ISERR(A1)
```

**Result:**
```
TRUE
```

### 2. #N/A Error (Not Detected):

If A1 contains `#N/A`:
```excel
=ISERR(A1)
```

**Result:**
```
FALSE (ISERR does not detect #N/A — use ISERROR or ISNA instead)
```

### 3. Valid Number:

If A1 contains `100`:
```excel
=ISERR(A1)
```

**Result:**
```
FALSE
```

### 4. #VALUE! Error:

If A1 contains a formula that results in `#VALUE!`:
```excel
=ISERR(A1)
```

**Result:**
```
TRUE
```

### 5. Conditional Error Handling:

```excel
=IF(ISERR(A1/B1), "Calculation error", A1/B1)
```

**Result:**
```
Returns "Calculation error" if the division produces an error (other than #N/A), otherwise returns the result
```

### 6. Separating #N/A from Other Errors:

```excel
=IF(ISERR(VLOOKUP(A1, D:E, 2, FALSE)), "Formula error", IF(ISNA(VLOOKUP(A1, D:E, 2, FALSE)), "Not found", VLOOKUP(A1, D:E, 2, FALSE)))
```

**Result:**
```
Distinguishes between lookup "Not found" (#N/A) and other formula errors
```

### 7. Combined with NOT for Non-Error Check:

```excel
=IF(NOT(ISERR(A1)), A1, 0)
```

**Result:**
```
Returns the value in A1 if it is not an error (or is #N/A), otherwise returns 0
```

### 8. Counting Error Cells in a Range:

```excel
=SUMPRODUCT(--ISERR(A1:A10))
```

**Result:**
```
Returns the number of cells in A1:A10 that contain errors other than #N/A
```

## Notes:

- `ISERR` is specifically designed to exclude `#N/A` from its error detection, unlike `ISERROR` which catches all errors.
- If you want to catch all errors including `#N/A`, use `ISERROR` instead.
- If you only want to detect `#N/A` errors, use `ISNA`.
- For simpler error handling, consider `IFERROR` (handles all errors) or `IFNA` (handles only `#N/A`).
- `ISERR` is part of the IS family of information functions (`ISBLANK`, `ISERR`, `ISERROR`, `ISNA`, `ISNUMBER`, `ISTEXT`, `ISLOGICAL`, etc.).
- When used inside `IF`, `ISERR` allows you to provide fallback values for formula errors while letting `#N/A` pass through for separate handling.

## Applications:

- **Selective Error Handling**: Trap calculation errors like `#DIV/0!` or `#VALUE!` while allowing `#N/A` to propagate for lookup-specific handling.
- **Data Validation**: Identify cells with formula errors that need correction, without flagging intentional `#N/A` markers.
- **Error Reporting**: Count or highlight non-`#N/A` errors in a dataset for auditing and troubleshooting.
- **Conditional Formatting**: Drive formula-based conditional formatting to highlight cells with calculation errors.
- **Robust Formulas**: Build layered error handling that distinguishes between "data not found" (`#N/A`) and "formula broken" (other errors).

## Related Functions:

- **ISERROR**: Returns TRUE if the value is any error, including `#N/A`.
- **ISNA**: Returns TRUE only if the value is the `#N/A` error.
- **IFERROR**: Returns a specified value if a formula evaluates to any error; otherwise returns the formula result.
- **IFNA**: Returns a specified value if a formula evaluates to `#N/A`; otherwise returns the formula result.
- **ISBLANK**: Returns TRUE if the cell is empty.
- **ISNUMBER**: Returns TRUE if the value is a number.
- **ISTEXT**: Returns TRUE if the value is text.
- **TYPE**: Returns a numeric code indicating the data type of a value.

> **Tip:** Use `ISERR` when you need to handle formula errors separately from lookup failures. A common pattern is to use `ISERR` for catching calculation errors (like `#DIV/0!` or `#VALUE!`) while using `ISNA` or `IFNA` to handle missing data from `VLOOKUP` or `XLOOKUP`. If you don't need to distinguish between error types, `IFERROR` is a simpler alternative that catches everything.