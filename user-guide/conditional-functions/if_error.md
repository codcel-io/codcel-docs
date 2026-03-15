<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IFERROR Function

The `IFERROR` function in Excel is used to catch errors in a formula and replace them with a specified alternative value. This is particularly useful for handling common errors like `#DIV/0!`, `#N/A`, `#VALUE!`, and others, making your spreadsheets cleaner and more user-friendly.

### Syntax:

    IFERROR(value, value_if_error)

- **value**: The formula or expression that you want to check for an error.
- **value_if_error**: The value to return if an error is found in the `value` argument. This can be text, numbers, or even another formula.

### Examples:

1. `=IFERROR(A1/B1, "Error in Calculation")` would return the result of `A1/B1` unless it results in an error, in which case it would display `"Error in Calculation"`.
2. `=IFERROR(VLOOKUP(E2, A2:B10, 2, FALSE), "Not Found")` would attempt to find `E2` in the range `A2:B10`. If the value is not found, which normally results in a `#N/A` error, it will return `"Not Found"` instead.
3. `=IFERROR(1/0, 0)` would normally result in a `#DIV/0!` error because of division by zero, but with `IFERROR`, it will return `0`.

### Usage Notes:
- `IFERROR` is a straightforward way to handle errors in Excel formulas and can improve the readability of the results.
- It is especially useful when your spreadsheet relies on data that might not always be complete or well-structured.
- Keep in mind that `IFERROR` will mask all errors, not just specific ones, so it's important to ensure that this general error handling is appropriate for your needs.

> **Note**: `IFERROR` only works for formulas that return an error. If you need to handle specific types of errors differently, you might need to use a combination of `IF` with `ISERROR` or `ISERR`.