<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ISERROR Function

The `ISERROR` function in Excel is used to **check whether a value is any error**. It returns TRUE if the value is any error type — including #N/A, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, and #NULL! — and FALSE for all non-error values. This function is useful for trapping all errors in formulas and providing fallback values or alternative logic when errors occur.

## Key Features of `ISERROR`:

- Returns `TRUE` for **any** error value, including `#N/A`, `#VALUE!`, `#REF!`, `#DIV/0!`, `#NUM!`, `#NAME?`, and `#NULL!`.
- Returns `FALSE` for non-error values (numbers, text, logicals, blanks).
- Commonly used with `IF` to substitute default values or trigger actions when any formula error occurs.
- Catches all error types, unlike `ISERR` which excludes `#N/A`.
- For simpler error handling, consider `IFERROR`, which combines the error check and fallback into a single function.

## Syntax:

```plaintext
ISERROR(value)
```

- **value**: The value or expression you want to test for an error. Typically a cell reference or formula result.

## How `ISERROR` Works:

1. `ISERROR` evaluates the provided value or expression.
2. If the result is any error value — `#N/A`, `#VALUE!`, `#REF!`, `#DIV/0!`, `#NUM!`, `#NAME?`, or `#NULL!` — it returns `TRUE`.
3. If the result is any non-error value (number, text, logical, blank), it returns `FALSE`.

## Examples:

### 1. Division by Zero Error:

If A1 contains a formula that results in `#DIV/0!`:
```excel
=ISERROR(A1)
```

**Result:**
```
TRUE
```

### 2. #N/A Error:

If A1 contains `#N/A`:
```excel
=ISERROR(A1)
```

**Result:**
```
TRUE (unlike ISERR, ISERROR detects #N/A as well)
```

### 3. Valid Number:

If A1 contains `100`:
```excel
=ISERROR(A1)
```

**Result:**
```
FALSE
```

### 4. #VALUE! Error:

If A1 contains a formula that results in `#VALUE!`:
```excel
=ISERROR(A1)
```

**Result:**
```
TRUE
```

### 5. Text Value:

If A1 contains `"Hello"`:
```excel
=ISERROR(A1)
```

**Result:**
```
FALSE
```

### 6. Conditional Error Handling:

```excel
=IF(ISERROR(A1/B1), "Error", A1/B1)
```

**Result:**
```
Returns "Error" if the division produces any error, otherwise returns the result
```

### 7. Protecting a VLOOKUP:

```excel
=IF(ISERROR(VLOOKUP(A1, D:E, 2, FALSE)), "Not found", VLOOKUP(A1, D:E, 2, FALSE))
```

**Result:**
```
Returns "Not found" if VLOOKUP fails with any error, otherwise returns the lookup result
```

### 8. Counting Error Cells in a Range:

```excel
=SUMPRODUCT(--ISERROR(A1:A10))
```

**Result:**
```
Returns the number of cells in A1:A10 that contain any error
```

## Notes:

- `ISERROR` catches **all** error types, including `#N/A`. If you want to exclude `#N/A` from detection, use `ISERR` instead.
- If you only want to detect `#N/A` errors, use `ISNA`.
- For simpler error handling, consider `IFERROR` (handles all errors in a single function) or `IFNA` (handles only `#N/A`).
- `ISERROR` is part of the IS family of information functions (`ISBLANK`, `ISERR`, `ISERROR`, `ISNA`, `ISNUMBER`, `ISTEXT`, `ISLOGICAL`, etc.).
- When used with `IF`, `ISERROR` evaluates the expression twice (once for the test and once for the result). `IFERROR` is more efficient as it evaluates only once.
- `ISERROR` returns `FALSE` for blank cells, since a blank cell is not an error.

## Applications:

- **Universal Error Handling**: Trap any error type in formulas and provide fallback values or messages.
- **Data Validation**: Identify cells with errors in a dataset for auditing and troubleshooting.
- **Conditional Formatting**: Drive formula-based conditional formatting to highlight cells containing any error.
- **Robust Formulas**: Prevent errors from cascading through dependent formulas by catching them early.
- **Error Reporting**: Count or flag all error cells in a range for quality assurance.

## Related Functions:

- **ISERR**: Returns TRUE if the value is any error **except** `#N/A`.
- **ISNA**: Returns TRUE only if the value is the `#N/A` error.
- **IFERROR**: Returns a specified value if a formula evaluates to any error; otherwise returns the formula result.
- **IFNA**: Returns a specified value if a formula evaluates to `#N/A`; otherwise returns the formula result.
- **ISBLANK**: Returns TRUE if the cell is empty.
- **ISNUMBER**: Returns TRUE if the value is a number.
- **ISTEXT**: Returns TRUE if the value is text.
- **TYPE**: Returns a numeric code indicating the data type of a value.

> **Tip:** In modern Excel, `IFERROR` is generally preferred over `IF(ISERROR(...), ...)` because it is more concise and more efficient — it evaluates the expression only once. However, `ISERROR` remains useful when you need to use the error check result in more complex logical expressions, or when combining with other IS functions to distinguish between different error types.