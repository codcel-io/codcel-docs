<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IFNA Function

The `IFNA` function in Excel returns a specified value if a formula evaluates to the `#N/A` error; otherwise, it returns the result of the formula. Unlike `IFERROR`, which catches all error types, `IFNA` targets only `#N/A` errors, allowing other errors to surface so they can be identified and corrected.

This function is especially useful when working with lookup functions like `VLOOKUP`, `HLOOKUP`, `MATCH`, and `INDEX`, where a `#N/A` error commonly indicates that a search value was not found.

### Key Features of IFNA:

- Catches only `#N/A` errors, leaving other error types (such as `#DIV/0!`, `#VALUE!`, `#REF!`) visible.
- Provides a cleaner alternative to `IF(ISNA(...), ...)` formulas.
- Works seamlessly with lookup functions to handle missing values gracefully.
- Keeps error detection precise by not masking unexpected errors.
- Simplifies formulas that need targeted `#N/A` handling without suppressing all errors.

### Syntax:

```plaintext
IFNA(value, value_if_na)
```

- **value**: The formula or expression to evaluate. This is typically a lookup function or any formula that might return `#N/A`.
- **value_if_na**: The value to return if the `value` argument evaluates to `#N/A`. This can be text, a number, a blank string (`""`), or another formula.

### How IFNA Works:

The `IFNA` function evaluates its arguments in a straightforward sequence:

1. Evaluates the **value** argument (the formula or expression).
2. If the result is a `#N/A` error, returns the **value_if_na** argument instead.
3. If the result is any other value — including other error types like `#DIV/0!`, `#VALUE!`, or `#REF!` — returns that result as-is.

This selective behavior is the key difference between `IFNA` and `IFERROR`. Where `IFERROR` replaces all errors, `IFNA` only replaces `#N/A`, ensuring that genuine formula errors are not hidden.

### Examples:

1. **Basic VLOOKUP with IFNA**:
   Search for a product name in a lookup table, returning "Not Found" if the product does not exist:
   `=IFNA(VLOOKUP("Widget", A1:B10, 2, FALSE), "Not Found")`
   If "Widget" is not in the range `A1:A10`, VLOOKUP returns `#N/A`.
   **Result**: `Not Found`

2. **MATCH with IFNA**:
   Find the position of a value in a list, returning `0` if it is not found:
   `=IFNA(MATCH("Blue", C1:C20, 0), 0)`
   If "Blue" is not in the range `C1:C20`, MATCH returns `#N/A`.
   **Result**: `0`

3. **Non-#N/A Errors Pass Through**:
   When a formula produces a different error type, IFNA does not catch it:
   `=IFNA(1/0, "Handled")`
   Division by zero produces a `#DIV/0!` error, which is not `#N/A`.
   **Result**: `#DIV/0!`

4. **INDEX-MATCH with IFNA**:
   Look up an employee's department, providing a default when the employee is not found:
   `=IFNA(INDEX(B1:B50, MATCH("Jane", A1:A50, 0)), "Unknown Department")`
   If "Jane" is not in `A1:A50`, MATCH returns `#N/A`, and IFNA catches it.
   **Result**: `Unknown Department`

5. **Combining IFNA with Other Functions**:
   Use IFNA inside a larger formula to substitute a default value in a calculation:
   `=SUM(D1:D5) + IFNA(VLOOKUP(E1, A1:B10, 2, FALSE), 0)`
   If the lookup fails with `#N/A`, the value `0` is used in the sum instead of causing an error.
   **Result**: The sum of `D1:D5` plus the lookup result (or `0` if not found).

6. **Returning a Blank Instead of an Error**:
   Suppress the `#N/A` display by returning an empty string:
   `=IFNA(HLOOKUP("Q1", A1:D2, 2, FALSE), "")`
   If "Q1" is not found in the first row, the cell appears blank instead of showing `#N/A`.
   **Result**: *(empty cell)*

7. **Nested IFNA for Multiple Lookups**:
   Try multiple lookups in sequence, falling back to each one:
   `=IFNA(VLOOKUP(A1, Table1, 2, FALSE), IFNA(VLOOKUP(A1, Table2, 2, FALSE), "Not in either table"))`
   Searches `Table1` first. If not found, searches `Table2`. If still not found, returns the fallback text.
   **Result**: The matched value from whichever table contains it, or `Not in either table`.

### Notes:

- `IFNA` is available in Excel 2013, Excel 2016, Excel 2019, Excel 365, and later versions.
- Use `IFNA` instead of `IFERROR` when you only want to handle `#N/A` errors and need other errors to remain visible for debugging.
- `IFNA` evaluates the **value** argument only once, making it more efficient than writing `IF(ISNA(value), value_if_na, value)`, which evaluates the formula twice.
- If you need to handle all error types, use `IFERROR` instead.
- Nesting `IFNA` inside `IFERROR` (or vice versa) allows you to handle `#N/A` differently from other errors: `=IFERROR(IFNA(formula, "No match"), "Other error")`.
- The **value_if_na** argument is only evaluated if the **value** argument actually returns `#N/A`, avoiding unnecessary computation.

### Related Functions:

- **IFERROR**: Returns a specified value if any error occurs; otherwise returns the formula result.
  Example: `=IFERROR(A1/B1, 0)` returns `0` if the division causes any error.

- **ISNA**: Returns `TRUE` if a value is the `#N/A` error; otherwise returns `FALSE`.
  Example: `=ISNA(VLOOKUP("X", A1:B5, 2, FALSE))` returns `TRUE` if the lookup fails with `#N/A`.

- **ISERROR**: Returns `TRUE` if a value is any error type; otherwise returns `FALSE`.
  Example: `=ISERROR(A1/0)` returns `TRUE` because division by zero produces `#DIV/0!`.

- **IF**: Evaluates a condition and returns one value for TRUE and another for FALSE.
  Example: `=IF(A1 > 100, "High", "Low")` returns `"High"` or `"Low"` based on the value.

- **VLOOKUP**: Searches for a value in the first column of a range and returns a value from a specified column.
  Example: `=VLOOKUP("Apple", A1:B10, 2, FALSE)` returns the value in column B for the row matching "Apple".

### Summary:

The `IFNA` function provides targeted handling for `#N/A` errors without masking other error types that may indicate genuine problems in your formulas. It is the preferred choice over `IFERROR` when working with lookup functions where a missing match is expected and should be handled gracefully, while other errors like `#DIV/0!` or `#REF!` should still be visible for troubleshooting.

By catching only `#N/A`, IFNA strikes the right balance between clean output and transparent error reporting, making it an essential tool for building robust and maintainable spreadsheets.