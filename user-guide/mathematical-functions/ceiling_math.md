<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CEILING.MATH Function

The `CEILING.MATH` function in Excel rounds a number up to the nearest multiple of a specified factor. It's an enhancement of the older `CEILING` function, providing more control and flexibility in the rounding process, especially with regard to handling negative numbers.

### Syntax:

    CEILING.MATH(number, [significance], [mode])


- **number**: The value you want to round.
- **significance** (optional): The multiple to which you want to round. If omitted, the default is 1.
- **mode** (optional): A value that defines the rounding direction. If omitted or set to 0, the function rounds up. If set to -1, the function rounds away from zero.

### Examples:

1. `=CEILING.MATH(4.1, 0.5)` would return `4.5` because 4.1 rounded up to the nearest 0.5 is 4.5.
2. `=CEILING.MATH(-4.1, 0.5)` would return `-4.0`. Unlike the traditional `CEILING` function, `CEILING.MATH` rounds negative numbers up (toward zero) by default.
3. `=CEILING.MATH(-4.1, 0.5, -1)` would return `-4.5`, as the `-1` mode forces the function to round away from zero.

> **Note**: The primary distinction between `CEILING.MATH` and the traditional `CEILING` function is the handling of negative numbers and the additional `mode` parameter for more rounding control.