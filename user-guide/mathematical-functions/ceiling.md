<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CEILING Function

The `CEILING` function in Excel rounds a number up to the nearest multiple of a specified factor. This can be especially useful in situations like determining the nearest whole number or rounding up to the nearest 0.5.

### Syntax:

    CEILING(number, significance)


- **number**: The value you want to round up.
- **significance**: The multiple to which you want to round up the number.

### Examples:

1. `=CEILING(4.1, 0.5)` would return `4.5` because 4.1 rounded up to the nearest 0.5 is 4.5.
2. `=CEILING(7, 5)` would return `10` because 7 rounded up to the nearest multiple of 5 is 10.
3. `=CEILING(-4.1, 0.5)` would return `-4.0`, as negative numbers are rounded away from zero.

> **Note**: The **number** and **significance**: If one is positive and the other is negative, the function fails.