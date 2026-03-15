<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SEC(number)

- **number**: The angle in radians for which you want to calculate the secant. This must be a numeric value.

### Description:

The `SEC` function returns the secant of a given angle. The secant is the reciprocal of the cosine, and is calculated
as:

    SEC(number) = 1 / COS(number)

### Examples:

1. `=SEC(PI()/3)` would return `2` because the cosine of π/3 is 0.5, and the reciprocal of 0.5 is 2.

2. `=SEC(PI()/4)` would return `√2` (approximately 1.414) because the cosine of π/4 is √2/2, and its reciprocal is √2.

3. `=SEC(0)` would return `1` because the cosine of 0 is 1, and its reciprocal is also 1.

4. `=SEC(PI())` returns `#DIV/0!` because the cosine of π is 0, and division by zero is undefined.

> **Note**:
> - The input must be in radians. If your data is in degrees, convert it first using the `RADIANS` function.
> - If the input leads to a cosine of 0 (like π/2, 3π/2, etc.), the function will return a `#DIV/0!` error.