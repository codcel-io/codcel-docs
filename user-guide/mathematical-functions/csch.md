<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CSCH Function

The `CSCH` function in Excel is used to calculate the **hyperbolic cosecant** of a given number. The hyperbolic cosecant
of a number is defined as the reciprocal of the hyperbolic sine of the number.

Mathematically, it can be expressed as:

    CSCH(x) = 1 / SINH(x)

where `SINH(x)` is the hyperbolic sine of the number `x`.

This function is useful in various mathematical, scientific, and engineering computations involving hyperbolic
functions.

### Syntax:

    CSCH(number)

- **number**: This is a required argument. It specifies the number for which the hyperbolic cosecant should be
  calculated.

### Key Points:

- The `CSCH` function operates on **real numbers**.
- If the value of `number` is `0`, the `CSCH` function will return a `#DIV/0!` error, as division by zero is undefined.
- The function evaluates input directly without the need for unit conversion like radians or degrees.

### Examples:

1. `=CSCH(1)`  
   Calculates the hyperbolic cosecant of `1`.  
   **Result**: `0.8509181283`

2. `=CSCH(0.5)`  
   Calculates the hyperbolic cosecant of `0.5`.  
   **Result**: `1.919034751`

3. `=CSCH(0)`  
   As the hyperbolic sine of `0` is `0`, the `CSCH` function will throw a divide-by-zero error.  
   **Result**: `#DIV/0!`

### Notes:

- Ensure the input `number` is a real number. Avoid using `0` as an input, as this will lead to undefined behavior.
- The `CSCH` function is especially useful in computations involving hyperbolic trigonometric functions.

> **Tip**: Use the `CSCH` function when dealing with reciprocal hyperbolic functions in your calculations. Be cautious
of input values that result in undefined behavior.