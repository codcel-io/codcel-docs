<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ATAN Function

The `ATAN` function in Excel returns the arctangent (or inverse tangent) of a number. The result, in radians, lies between `-π/2` and `π/2`. Essentially, the function gives you the angle whose tangent is the specified number.

### Syntax:

    ATAN(number)


- **number**: This is a required argument. It represents the tangent of the angle you want to find.

### Examples:

1. `=ATAN(1)` would return an angle in radians, which is approximately 0.7854 (or 45° when converted to degrees).
2. `=ATAN(0)` would return 0, as the arctangent of 0 is 0.
3. `=ATAN(A1)` would return the arctangent of the number in cell A1.

> **Note**: If you're interested in obtaining the result in degrees instead of radians, you can use the formula `=DEGREES(ATAN(number))`.