<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ACOS Function

The `ACOS` function in Excel returns the arccosine (or inverse cosine) of a number. The result, in radians, is between `0` and `π`. Essentially, it's the angle whose cosine is the specified number.

### Syntax:

    ACOS(number)

- **number**: This is a required argument. It must be a numeric value between `-1` and `1` (inclusive).

### Examples:

1. `=ACOS(0.5)` would return an angle in radians, approximately 1.0472 (or 60° when converted to degrees).
2. `=ACOS(-1)` would return π (approximately 3.1416 radians, or 180°).
3. `=ACOS(A1)` would return the arccosine of the number in cell A1, provided the value in A1 is within the valid range.

> **Note**: If you want the result in degrees instead of radians, you can use the formula `=DEGREES(ACOS(number))`.