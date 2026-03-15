<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## INT Function

The `INT` function in Excel is used to round a number down to the nearest integer. The function effectively truncates any fractional component of the number and returns the largest integer less than or equal to the specified value.

### Syntax:

    INT(number)


- **number**: The numeric value you want to round down to the nearest integer.

### Examples:

1. `=INT(8.9)` would return `8`. The fractional part `.9` is removed, leaving the integer part `8`.
2. `=INT(-3.7)` would return `-4`. For negative numbers, `INT` rounds away from zero.
3. `=INT(4)` would simply return `4`, as the number is already an integer.

### Usage Notes:
- The `INT` function is different from the `ROUND`, `ROUNDUP`, and `ROUNDDOWN` functions in that it always rounds a number down towards the nearest integer.
- For positive numbers, `INT` and `ROUNDDOWN` function similarly. However, their behavior differs for negative numbers, as `ROUNDDOWN` rounds towards zero.
- The `INT` function can be used in various scenarios, such as when working with time calculations or in scenarios where only the integer part of a number is required.

> **Note**: In scenarios where you need to round a number up to the nearest integer, you can use the `CEILING` function or, for more specific control, the `ROUNDUP` function.