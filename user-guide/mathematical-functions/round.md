<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ROUND Function

The `ROUND` function in Excel is used to round a number to a specified number of digits.

### Syntax:

    ROUND(number, num_digits)

- **number**: This is the number you want to round.
- **num_digits**: This specifies the number of digits to which you want to round.
    - If `num_digits` is greater than 0, the number is rounded to the specified number of decimal places.
    - If `num_digits` is 0, the number is rounded to the nearest whole number.
    - If `num_digits` is less than 0, the number is rounded to the left of the decimal point.

### Examples:

1. `=ROUND(123.4567, 2)` would return 123.46.
2. `=ROUND(123.4567, 0)` would return 123.
3. `=ROUND(123.4567, -2)` would return 100.

It's important to note that the `ROUND` function follows the standard rules of rounding. Numbers equal to or greater than 5 will round up, and numbers less than 5 will round down.