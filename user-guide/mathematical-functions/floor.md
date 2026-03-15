<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FLOOR Function

The `FLOOR` function in Excel rounds a number down, towards zero, to the nearest specified multiple. This can be useful
for standardizing values or ensuring they align with a specific interval.

### Syntax:

    FLOOR(number, significance)

- **number**: The numeric value that you want to round down.
- **significance**: The multiple to which the number is to be rounded. The value must have the same sign as the number
  or an error will occur.

### Examples:

1. `=FLOOR(7.2, 2)` would return `6`, since `7.2` is rounded down to the nearest multiple of `2`.
2. `=FLOOR(-7.2, 2)` would return `-8`, as `-7.2` is rounded down to the nearest multiple of `2` (directionally towards
   zero).
3. `=FLOOR(6.5, 0.5)` returns `6.5`, because `6.5` is already aligned with a multiple of `0.5`.
4. `=FLOOR(5.7, 1)` returns `5`, rounding `5.7` down to the nearest whole number.

### Usage Notes:

- If the **significance** argument is omitted, Excel defaults it to `1`, and the number will be rounded to the nearest
  integer below it.
- The function will raise an error if the **number** and **significance** have opposite signs.
- Negative numbers are rounded down (towards zero) to the nearest multiple with the appropriate magnitude.
- The `FLOOR` function is particularly useful for standardizing numeric values to a given interval, often in finance,
  engineering, and pricing calculations.

> **Tip**: Consider using `FLOOR.MATH` or `FLOOR.PRECISE` for additional flexibility and more advanced control over
> rounding operations!