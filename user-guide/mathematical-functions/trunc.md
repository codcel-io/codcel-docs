<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TRUNC Function

The `TRUNC` (truncate) function in Excel is used to truncate a number to an integer by removing the fractional part of the number. Unlike the `ROUND`, `ROUNDUP`, and `ROUNDDOWN` functions, `TRUNC` simply cuts off the decimal without any rounding.

### Syntax:

    TRUNC(number, [num_digits])

- **number**: The numeric value you want to truncate.
- **num_digits** (optional): Specifies the precision of the truncation. If omitted, it defaults to 0 (zero), which means truncating to the nearest whole number. If a positive number, `TRUNC` will leave that many digits after the decimal point. If a negative number, it truncates off digits to the left of the decimal point.

### Examples:

1. `=TRUNC(8.9)` would return `8`. It simply removes the decimal part `.9`, leaving the integer `8`.
2. `=TRUNC(-3.7)` would return `-3`. Unlike `INT`, which rounds negative numbers down, `TRUNC` just removes the decimal part.
3. `=TRUNC(15.789, 1)` would return `15.7`, keeping one digit after the decimal point.

### Usage Notes:
- `TRUNC` is useful when you need to remove the fractional part of a number without rounding.
- It's particularly handy in financial calculations where fractional parts of a number are not valid, or when working with time calculations.
- The behavior of `TRUNC` is similar to `INT` for positive numbers, but it differs for negative numbers, as `INT` rounds negative numbers down.

> **Note**: The `TRUNC` function is often used when the goal is to discard the decimal portion of a number entirely, regardless of whether the remaining integer part is closer or farther to the original number.