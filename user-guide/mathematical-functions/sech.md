<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SECH(number)

- **number**: The angle in radians for which you want to calculate the hyperbolic secant. This must be a numeric value.

### Description:

The `SECH` function returns the hyperbolic secant of a given number. The hyperbolic secant is defined as:

    SECH(number) = 2 / (e^number + e^(-number))

Where `e` is the base of natural logarithms (approximately 2.718).

### Examples:

1. `=SECH(0)` would return `1` because the exponential functions cancel each other out, resulting in SECH(0) = 2 / (1 +
   1) = 1.

2. `=SECH(1)` would return approximately `0.648` because SECH(1) = 2 / (e + e^(-1)).

3. `=SECH(-1)` would also return approximately `0.648` since the hyperbolic secant is symmetric around 0.

4. `=SECH(2)` would return approximately `0.265` because SECH(2) = 2 / (e^2 + e^(-2)).

### Notes:

- The `SECH` function expects the input to be in radians. If the value is in degrees, convert it to radians using the
  `RADIANS` function before using `SECH`.
- If the input number is very large (positive or negative), the `SECH` function will approach zero.