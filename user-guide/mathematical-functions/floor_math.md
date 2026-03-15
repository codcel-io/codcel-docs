<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FLOOR.MATH Function

The `FLOOR.MATH` function in Excel is used to round a number down to the nearest specified multiple. This function
provides additional flexibility compared to the basic `FLOOR` function, allowing better control over how rounding
behaves with negative numbers.

### Syntax:

    FLOOR.MATH(number, [significance], [mode])

- **number**: The numeric value that you want to round down.
- **significance** (optional): The multiple to which the number is rounded. By default, this is `1`.
- **mode** (optional): Determines how negative numbers are rounded. If `mode` is non-zero or omitted, negative numbers
  are rounded away from zero toward negative infinity. If `mode` is `0`, negative numbers are rounded toward zero.

### Examples:

1. `=FLOOR.MATH(7.9)`  
   Returns `7`, as `7.9` is rounded down to the nearest whole number.

2. `=FLOOR.MATH(7.9, 2)`  
   Returns `6`, since `7.9` is rounded down to the nearest multiple of `2`.

3. `=FLOOR.MATH(-7.1)`  
   Returns `-8`, as negative numbers are rounded down away from zero by default.

4. `=FLOOR.MATH(-7.1, 2, 0)`  
   Returns `-6`, as the `mode` argument (`0`) changes the behavior, causing the number to round towards zero.

5. `=FLOOR.MATH(-7.6, 3)`  
   Returns `-9`, because `-7.6` is rounded down (away from zero) to the nearest multiple of `3`.

### Usage Notes:

- When **significance** is omitted, the function defaults to rounding to the nearest integer (`significance = 1`).
- The **mode** argument is optional and primarily controls how rounding behaves for negative numbers. Setting `mode = 0`
  modifies negative number rounding to be closer to zero instead of away from it.
- For positive numbers, the `FLOOR.MATH` function behaves identically to `FLOOR`.
- This function is particularly useful in scenarios that involve standardizing numeric values, particularly in
  applications like accounting, engineering, scheduling, and data analysis.