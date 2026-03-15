<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LN Function

The `LN` function in Excel is used to calculate the natural logarithm of a given number. The natural logarithm is the
logarithm to the base `e` (approximately 2.718), which is a mathematical constant.

### Syntax:

    LN(number)

- **number**: The positive numeric value for which you want to calculate the natural logarithm.

### Examples:

1. `=LN(1)`  
   Returns `0`, because the natural logarithm of `1` is `0`.

2. `=LN(2.718)`  
   Returns approximately `1`, because `e^1 = 2.718`.

3. `=LN(7.389)`  
   Returns approximately `2`, because `e^2 = 7.389`.

4. `=LN(0.5)`  
   Returns a negative value, approximately `-0.693`, as `e^-0.693 ≈ 0.5`.

5. `=LN(10)`  
   Returns approximately `2.302`, because `e^2.302 ≈ 10`.

### Usage Notes:

- The **number** must be positive; otherwise, the function will return a `#NUM!` error.
- The function is undefined for non-positive values (i.e., `0` or negative numbers).
- The `LN` function is widely used in mathematics, finance, and science, particularly for exponential growth or decay
  problems, compound interest calculations, and solving for time in natural exponential relationships.
- For logarithms with other bases, use the `LOG` function in Excel, which allows specifying a different base.