<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## QUOTIENT Function

The `QUOTIENT` function in Excel returns the integer portion of a division by discarding the remainder. It is useful when you need only the whole number result of a division operation.

### Syntax:

    QUOTIENT(numerator, denominator)

- **numerator**: The number to be divided.
- **denominator**: The number by which you want to divide the numerator.

### Examples:

1. `=QUOTIENT(10, 3)` would return `3` because 10 divided by 3 equals 3 with a remainder of 1, and the remainder is discarded.

2. `=QUOTIENT(25, 4)` would return `6` because 25 divided by 4 equals 6 with a remainder of 1.

3. `=QUOTIENT(-10, 3)` would return `-3` because the function also works with negative numbers.

> **Note**: If you need the remainder of a division, use the `MOD` function. For example, `MOD(10, 3)` would return `1` as the remainder.