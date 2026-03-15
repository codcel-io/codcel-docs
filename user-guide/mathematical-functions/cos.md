<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COS Function

The `COS` function in Excel returns the cosine of a given angle. This function expects the angle to be provided in radians. If you have an angle in degrees and need to convert it to radians, you can use the `RADIANS` function.

### Syntax:

    COS(number)

- **number**: The angle in radians for which you want the cosine.

### Examples:

1. `=COS(0)` would return `1`, since the cosine of 0 radians is 1.
2. If you have an angle of 60 degrees and want to find its cosine, you can combine the `RADIANS` and `COS` functions: `=COS(RADIANS(60))` would return `0.5`.

> **Note**: Trigonometric functions like `COS` can be instrumental in engineering, physics, and other fields where calculations involving angles and circular motion are required.