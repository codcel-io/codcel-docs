<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    TAN(number)

- **number**: This represents the angle (in radians) for which you want to calculate the tangent.

### Description:

The `TAN` function in Excel returns the tangent of a given angle provided in radians. The tangent of an angle is the
ratio of the sine of the angle to the cosine of the angle, mathematically represented as:

    TAN(number) = sin(number) / cos(number)

### Examples:

1. `=TAN(0)` would return `0`, because the tangent of 0 radians is 0.
2. `=TAN(PI()/4)` would return `1`, because the tangent of π/4 radians (45 degrees) is 1.
3. `=TAN(-PI()/4)` would return `-1`, because the tangent of -π/4 radians (-45 degrees) is -1.
4. `=TAN(PI()/2)` would return a very large value (or an error in some cases), as the tangent of π/2 radians (90
   degrees) approaches infinity.
5. `=TAN(3*PI()/4)` would return `-1`, because the tangent of 3π/4 radians (135 degrees) is -1.

### Notes:

- The `TAN` function requires the input angle to be in radians. If your angle is in degrees, convert it to radians by
  using the `RADIANS` function, e.g., `TAN(RADIANS(angle_in_degrees))`.
- The result of the `TAN` function will become undefined (or very large) when the cosine of the given angle is 0, such
  as at π/2 + nπ (90 degrees, 270 degrees, etc.).
- It is commonly used in trigonometry, physics, engineering, and geometry for ratio-based angle calculations.