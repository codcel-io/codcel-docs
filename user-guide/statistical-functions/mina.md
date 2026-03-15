<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MINA Function

The `MINA` function in Excel returns the **smallest value** in a set of values, including logical values and text
representations of numbers. Unlike the `MIN` function, `MINA` evaluates `TRUE` as `1`, `FALSE` as `0`, and text
representations of numbers as numbers.

### Key Features of MINA:

- It includes logical values and text in its evaluation:
    - `TRUE` is treated as `1`.
    - `FALSE` is treated as `0`.
    - Text values that cannot be interpreted as numbers are treated as `0`.
- Numeric values are evaluated as they are.
- Empty cells are ignored.

This function is particularly useful when you want to find the minimum value in a dataset that includes logical values
or mixed data types.

### Syntax:

```plaintext
MINA(value1, [value2], ...)
```

- **value1, [value2], ...**: These are the values, references, or ranges you want to find the minimum for. The `value1`
  argument is required, while subsequent arguments are optional.

### Examples:

1. `=MINA(10, 20, 30, TRUE)`
   Returns the smallest value among `10, 20, 30` and includes `TRUE` as `1` in the evaluation.
   **Result**: `1`

2. `=MINA(5, 10, FALSE, "Hello")`
   Considers `FALSE` as `0` and `"Hello"` as `0`, then returns the smallest value.
   **Result**: `0`

3. `=MINA(A1:A5)`
   Returns the smallest value in the range `A1:A5`, including logical values or text representations if present.

### Notes:

- The `MINA` function extends the traditional `MIN` by providing support for logical and text values, making it useful
  for mixed data types.
- If no numeric, logical, or text values are found, `MINA` returns `0`.
- Error values within the arguments will cause the function to return an error.
- `MINA` differs from `MIN` in that `MIN` ignores logical values and text, while `MINA` includes them in the
  evaluation.

> **Tip**: Use `MINA` instead of `MIN` when your data contains logical values or text that you want to factor into
finding the minimum value. For the corresponding maximum function, see `MAXA`.