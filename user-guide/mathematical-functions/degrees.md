<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DEGREES Function

The `DEGREES` function in Excel is used to convert radians into degrees. It's the counterpart to the `RADIANS` function and is beneficial when you have an angle in radians but need its measurement in degrees.

### Syntax:

    DEGREES(angle)

- **angle**: The angle in radians that you want to convert to degrees.

### Examples:

1. `=DEGREES(π)` or `=DEGREES(3.14159)` would return `180`, since π radians is equivalent to 180 degrees.
2. `=DEGREES(π/2)` or `=DEGREES(1.5708)` would return `90`, as π/2 radians is equivalent to 90 degrees.

> **Note**: The `DEGREES` function is especially useful when interpreting the results of trigonometric calculations in Excel that produce results in radians but need to be expressed in degrees.