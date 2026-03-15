<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MAXA Function

The `MAXA` function in Excel returns the **largest value** in a set of values, including logical values and text
representations of numbers. Unlike the `MAX` function, `MAXA` evaluates `TRUE` as `1`, `FALSE` as `0`, and text
representations of numbers as numbers.

### Key Features of MAXA:

- It includes logical values and text in its evaluation:
    - `TRUE` is treated as `1`.
    - `FALSE` is treated as `0`.
    - Text values that cannot be interpreted as numbers are treated as `0`.
- Numeric values are evaluated as they are.
- Empty cells are ignored.

This function is particularly useful when you want to find the maximum value in a dataset that includes logical values
or mixed data types.

### Syntax:

```plaintext
MAXA(value1, [value2], ...)
```

- **value1, [value2], ...**: These are the values, references, or ranges you want to find the maximum for. The `value1`
  argument is required, while subsequent arguments are optional.

### Examples:

1. `=MAXA(10, 20, 30, TRUE)`
   Returns the largest value among `10, 20, 30` and includes `TRUE` as `1` in the evaluation.
   **Result**: `30`

2. `=MAXA(-5, -10, FALSE, "Hello")`
   Considers `FALSE` as `0` and `"Hello"` as `0`, then returns the largest value.
   **Result**: `0`

3. `=MAXA(A1:A5)`
   Returns the largest value in the range `A1:A5`, including logical values or text representations if present.

### Notes:

- The `MAXA` function extends the traditional `MAX` by providing support for logical and text values, making it useful
  for mixed data types.
- If no numeric, logical, or text values are found, `MAXA` returns `0`.
- Error values within the arguments will cause the function to return an error.
- `MAXA` differs from `MAX` in that `MAX` ignores logical values and text, while `MAXA` includes them in the
  evaluation.

> **Tip**: Use `MAXA` instead of `MAX` when your data contains logical values or text that you want to factor into
finding the maximum value. For the corresponding minimum function, see `MINA`.