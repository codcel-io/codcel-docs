<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## AVERAGEA Function

The `AVERAGEA` function in Excel calculates the **average (arithmetic mean)** of the values in its arguments, treating
logical values and text differently compared to the `AVERAGE` function.

### Key Features of AVERAGEA:

- It includes text and logical values in its calculation:
    - `TRUE` is treated as `1`.
    - `FALSE` and text (non-numeric) values are treated as `0`.
- Numeric values are calculated as they are.

This function is particularly useful when you want to incorporate logical values or non-numeric data in your
calculations.

### Syntax:

```plaintext
AVERAGEA(value1, [value2], ...)
```

- **value1, [value2], ...**: These are the values or references you want to calculate the average for. The `value1`
  argument is required, while subsequent arguments are optional.

### Examples:

1. `=AVERAGEA(10, 20, 30, TRUE)`  
   Calculates the average of the numbers `10, 20, 30` and includes `TRUE` as `1` in the calculation.  
   **Result**: `15.25`

2. `=AVERAGEA(5, 10, "Hello", FALSE, 15)`  
   Considers `"Hello"` as `0`, `FALSE` as `0`, and calculates the average of the values.  
   **Result**: `6`

3. `=AVERAGEA(A1:A5)`  
   Computes the average for the range `A1:A5`, including logical values or texts if present.

### Notes:

- The `AVERAGEA` function extends the traditional `AVERAGE` by providing support for logical and text values during
  calculations, making it versatile for mixed data types.
- Error values or text that cannot be converted to numbers will result in an error.
- When only logical or text values are provided, the function will still return an average based on their
  representation (`TRUE` as `1`, `FALSE` as `0`, and text as `0`).

> **Tip**: Use `AVERAGEA` instead of `AVERAGE` when your data contains logical values or text that you want to factor
into the average calculation.