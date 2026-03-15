<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NOT Function

The `NOT` function in Excel is a logical function used to reverse the value of its argument. If given a logical value of `TRUE`, `NOT` returns `FALSE`; if given `FALSE`, it returns `TRUE`.

### Syntax:

    NOT(logical)

- **logical**: A logical value or expression that can be evaluated as `TRUE` or `FALSE`.

### Examples:

1. `=NOT(TRUE)` would return `FALSE`.
2. `=NOT(FALSE)` would return `TRUE`.
3. `=NOT(A1=B1)` would return `TRUE` if `A1` is not equal to `B1`, and `FALSE` if `A1` is equal to `B1`.

### Usage Notes:
- The `NOT` function is often used in conjunction with other logical functions like `IF`, `AND`, and `OR` to create more complex logical tests.
- It can be especially useful in scenarios where you need to conditionally apply formatting, perform calculations, or filter data based on the inverse of a given condition.

> **Note**: Since `NOT` only accepts a single logical argument, if you need to reverse multiple logical tests at once, you may need to use it in combination with `AND` or `OR`.