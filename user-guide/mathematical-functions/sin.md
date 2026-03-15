<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SIN(number)

- **number**: The angle in radians for which you want to calculate the sine. This must be a numeric value.

### Description:

The `SIN` function returns the sine of a given angle. The sine is a trigonometric function that represents the ratio of
the length of the side opposite the angle to the length of the hypotenuse in a right triangle.

    SIN(number) = opposite / hypotenuse

### Examples:

1. `=SIN(0)` would return `0` because the sine of 0 radians is 0.

2. `=SIN(PI()/2)` would return `1` because the sine of π/2 radians (90 degrees) is 1.

3. `=SIN(PI())` would return approximately `0` because the sine of π radians (180 degrees) is 0.

4. `=SIN(PI()/6)` would return approximately `0.5` because the sine of π/6 radians (30 degrees) is 0.5.

### Notes:

- The `SIN` function expects the input to be in radians. If the value is in degrees, convert it to radians using the
  `RADIANS` function before using `SIN`.
- The value of the sine function oscillates between `-1` and `1`.
- If the input number is very large, the function might lose precision, but it will still calculate the sine within a
  reasonable range.