<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SQRTPI(number)

- **number**: The numeric value for which you want to calculate the square root of (number × π). This must be a
  non-negative numeric value.

### Description:

The `SQRTPI` function returns the square root of the product of a given number and π (pi, approximately
3.14159265358979). For example:

    SQRTPI(number) = √(number × π)

### Examples:

1. `=SQRTPI(1)` would return approximately `1.772454`, because √(1 × π) = √π ≈ 1.772454.
2. `=SQRTPI(2)` would return approximately `2.506628`, because √(2 × π) ≈ 2.506628.
3. `=SQRTPI(0)` would return `0`, because √(0 × π) = 0.
4. `=SQRTPI(3.14)` would return approximately `3.137594`, because √(3.14 × π) ≈ 3.137594.
5. `=SQRTPI(4)` would return approximately `3.544908`, because √(4 × π) ≈ 3.544908.

### Notes:

- The `SQRTPI` function calculates the square root of the product of the provided number and π.
- It only works with non-negative numbers. If you provide a negative value, Excel will return a `#NUM!` error.
- It is commonly used in engineering, geometry, and physics calculations where π appears in mathematical formulas.
- The result of the `SQRTPI` function is always a non-negative value, as it calculates the principal (positive) square
  root.