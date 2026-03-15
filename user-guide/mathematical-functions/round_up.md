<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ROUNDUP Function

The `ROUNDUP` function in Excel is used to round a number up, away from zero, to a specified number of digits. Unlike the `ROUND` function, which can round either up or down based on the value of the digit being rounded, `ROUNDUP` always rounds numbers up.

### Syntax:

    ROUNDUP(number, num_digits)

- **number**: The number you want to round up.
- **num_digits**: The number of digits to which you want to round up the `number`. If `num_digits` is greater than 0 (zero), then the number is rounded up to the specified number of decimal places. If `num_digits` is 0, the number is rounded up to the nearest whole number. If `num_digits` is less than 0, the number is rounded up to the left of the decimal point.

### Examples:

1. `=ROUNDUP(3.14159, 3)` would return `3.142`. It rounds the number `3.14159` up to three decimal places.
2. `=ROUNDUP(-2.789, 1)` would return `-2.8`. Notice that it rounds away from zero, so negative numbers become more negative.
3. `=ROUNDUP(123.456, 0)` would return `124`. It rounds up to the nearest whole number.

### Usage Notes:
- `ROUNDUP` is useful when you need to ensure that the result of rounding does not underestimate the original value.
- This function can be particularly useful in financial calculations where it's essential to round towards higher values (e.g., when calculating interest, tax rates, or other financial metrics).

> **Note**: For rounding down regardless of the number's sign, use the `ROUNDDOWN` function.