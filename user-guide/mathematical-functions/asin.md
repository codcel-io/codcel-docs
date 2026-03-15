<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ASIN Function

The `ASIN` function in Excel returns the arcsine (or inverse sine) of a number. The result, in radians, is between `-π/2` and `π/2`. Essentially, it gives you the angle whose sine is the specified number.

### Syntax:

    ASIN(number)


- **number**: This is a required argument. It must be a numeric value between `-1` and `1` (inclusive), representing the sine of the angle you want to find.

### Examples:

1. `=ASIN(0.5)` would return an angle in radians, approximately 0.5236 (or 30° when converted to degrees).
2. `=ASIN(1)` would return `π/2` (approximately 1.5708 radians, or 90°).
3. `=ASIN(A1)` would return the arcsine of the number in cell A1, provided the value in A1 is within the valid range.

> **Note**: If you want the result in degrees rather than radians, you can combine the `ASIN` function with the `DEGREES` function like this: `=DEGREES(ASIN(number))`.