<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SINH(number)

- **number**: The number for which you want to calculate the hyperbolic sine. This must be a numeric value.

### Description:

The `SINH` function returns the hyperbolic sine of a given number. The hyperbolic sine is calculated using the formula:

    SINH(number) = (e^number - e^(-number)) / 2

Where `e` is the base of the natural logarithm (approximately 2.718281828459045).

### Examples:

1. `=SINH(0)` would return `0` because the hyperbolic sine of 0 is 0.

2. `=SINH(1)` would return approximately `1.175201` because `SINH(1) = (e^1 - e^(-1)) / 2`.

3. `=SINH(-1)` would return approximately `-1.175201` because `SINH(-1) = (e^(-1) - e^1) / 2`.

4. `=SINH(2)` would return approximately `3.62686`.

### Notes:

- The `SINH` function works with real numbers and returns real numbers.
- It is related to the hyperbolic cosine (`COSH`) and hyperbolic tangent (`TANH`) functions, which can be used to
  calculate other hyperbolic properties.
- The `SINH` function is available in most spreadsheet applications like Excel and follows standard mathematical
  conventions.
- The result of the function increases exponentially for large positive or negative inputs due to the exponential nature
  of the formula.