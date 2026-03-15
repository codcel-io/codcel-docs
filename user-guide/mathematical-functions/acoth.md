<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ACOTH Function

The `ACOTH` function in Excel returns the inverse hyperbolic cotangent of a number. It is used to calculate the arc
hyperbolic cotangent and works only for numbers which are greater than 1 or less than -1.

### Syntax:

    ACOTH(number)

- **number**: This is a required argument. It represents the value for which you want to calculate the inverse
  hyperbolic cotangent. The function is defined only for values greater than 1 or less than -1.

### Examples:

1. `=ACOTH(2)` would return approximately 0.5493.
2. `=ACOTH(-2)` would return approximately -0.5493.
3. `=ACOTH(A1)` would calculate the inverse hyperbolic cotangent of the value in cell A1 (provided the value in A1 is
   greater than 1 or less than -1).

> **Note**: If the input number is between -1 and 1 (inclusive), Excel will return a `#NUM!` error, as the inverse
hyperbolic cotangent is undefined in this range.