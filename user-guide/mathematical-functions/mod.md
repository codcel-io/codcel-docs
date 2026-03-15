<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MOD Function

The `MOD` function in Excel returns the remainder after a number (dividend) is divided by a divisor. It is useful for
finding what is left over after division.

### Syntax:

    MOD(number, divisor)

- **number**: This is a required argument. It represents the dividend, the number you want to divide.
- **divisor**: This is also a required argument. It is the number by which you want to divide the dividend.

### Examples:

1. `=MOD(10, 3)` would return `1`, since 10 divided by 3 is 3 with a remainder of 1.
2. `=MOD(15, 4)` would return `3`, since 15 divided by 4 is 3 with a remainder of 3.
3. `=MOD(A1, B1)` would return the remainder of dividing the number in cell A1 by the number in cell B1.

> **Note**: If the `divisor` is zero, the `MOD` function will return a `#DIV/0!` error because division by zero is
undefined.