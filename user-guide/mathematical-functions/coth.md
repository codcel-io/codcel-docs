<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COTH Function

The `COTH` function in Excel is used to calculate the **hyperbolic cotangent** of a given number. The hyperbolic
cotangent of a number is defined as the reciprocal of the hyperbolic tangent.

Mathematically, it can be expressed as:

    COTH(x) = 1 / TANH(x)

where `TANH(x)` is the hyperbolic tangent of the number `x`.

This function is useful in various mathematical, engineering, and computational applications.

### Syntax:

    COTH(number)

- **number**: This is a required argument. It specifies the value for which the hyperbolic cotangent should be
  calculated.

### Key Points:

- The `COTH` function operates on **real numbers**.
- For values of `number` greater than 0, `COTH(x)` will always be greater than 1.
- For values of `number` less than 0, `COTH(x)` will always be less than -1.
- At `number` = 0, the hyperbolic tangent becomes zero, resulting in an undefined behavior. Consequently, the `COTH`
  function will throw a `#DIV/0!` error.

### Examples:

1. `=COTH(1)`  
   Calculates the hyperbolic cotangent of `1`.  
   **Result**: `1.31304`

2. `=COTH(-2)`  
   Calculates the hyperbolic cotangent of `-2`.  
   **Result**: `-1.03731`

3. `=COTH(0)`  
   As the hyperbolic tangent of `0` is `0`, the `COTH` function divides by zero.  
   **Result**: `#DIV/0!`

### Notes:

- Ensure the input `number` is a real number.
- The `COTH` function is not directly available in older versions of Excel. In such cases, you can use the formula
  `1 / TANH(x)` to achieve the same result.
- If the input value is `0`, an error will occur because division by zero is undefined.

> **Tip**: Use the `COTH` function when working with hyperbolic functions in scientific and engineering calculations.
> Ensure all inputs are valid and handle zero cases carefully to avoid errors.