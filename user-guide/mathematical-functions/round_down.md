<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ROUNDDOWN Function

The `ROUNDDOWN` function in Excel is used to round a number down, toward zero, to a specified number of digits. Unlike the standard `ROUND` function, `ROUNDDOWN` always rounds numbers down.

### Syntax:

    ROUNDDOWN(number, num_digits)

- **number**: The number you want to round down.
- **num_digits**: The number of digits to which you want to round down the `number`.

### Examples:

1. `=ROUNDDOWN(3.14159, 3)` would return `3.141`. It rounds the number `3.14159` down to three decimal places.
2. `=ROUNDDOWN(-2.789, 1)` would return `-2.7`. Notice that even though it's a negative number, `ROUNDDOWN` still rounds towards zero.
3. `=ROUNDDOWN(123.456, 0)` would return `123`. It rounds down to the nearest whole number.

### Usage Notes:
- `ROUNDDOWN` differs from `ROUND` in that `ROUND` may round a number up or down depending on the fractional part, whereas `ROUNDDOWN` always rounds towards zero.
- This function can be useful when you need to truncate a number but keep it within the same sign as the original number.

> **Note**: For rounding up regardless of the number's sign, use the `ROUNDUP` function.