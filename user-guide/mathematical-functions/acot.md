<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ACOT Function

The `ACOT` function in Excel returns the arc cotangent (or inverse cotangent) of a number. The result, in radians, is
between `0` and `π` for positive numbers, or between `-π` and `0` for negative numbers. Essentially, it's the angle
whose cotangent is the specified number.

### Syntax:

    ACOT(number)

- **number**: This is a required argument. It represents the cotangent value for which you want to calculate the inverse
  cotangent.

### Examples:

1. `=ACOT(1)` would return an angle in radians, approximately 0.7854 (or 45° when converted to degrees).
2. `=ACOT(0)` would return π/2 (approximately 1.5708 radians, or 90°).
3. `=ACOT(-1)` would return an angle in radians, approximately -0.7854 (or -45° when converted to degrees).
4. `=ACOT(A1)` would return the arc cotangent of the number in cell A1.

> **Note**: If you want the result in degrees instead of radians, you can use the formula `=DEGREES(ACOT(number))`.