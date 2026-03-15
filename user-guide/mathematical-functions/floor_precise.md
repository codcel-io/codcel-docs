<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FLOOR.PRECISE Function

The `FLOOR.PRECISE` function in Excel is used to round a number down to the nearest multiple of a specified
significance. It ensures precision and consistency, especially when dealing with both positive and negative numbers, by
always rounding towards zero.

### Syntax:

    FLOOR.PRECISE(number, [significance])

- **number**: The numeric value that you want to round down.
- **significance** (optional): The multiple to which the number is rounded. By default, this is `1`.

### Key Characteristics:

- Unlike the `FLOOR` function, `FLOOR.PRECISE` behaves exactly the same regardless of the sign of the number.
- It always rounds down numerically (towards zero) to the nearest multiple of the provided significance.
- It is particularly useful for applications requiring consistent rounding logic.

### Examples:

1. `=FLOOR.PRECISE(7.9)`  
   Returns `7`, as `7.9` is rounded down to the nearest whole number.

2. `=FLOOR.PRECISE(7.9, 2)`  
   Returns `6`, as `7.9` is rounded down to the nearest multiple of `2`.

3. `=FLOOR.PRECISE(-7.8)`  
   Returns `-7`, as `-7.8` is rounded numerically down to the nearest whole number (towards zero).

4. `=FLOOR.PRECISE(-7.8, 2)`  
   Returns `-6`, as `-7.8` is rounded numerically down to the nearest multiple of `2` (towards zero).

### Usage Notes:

- When the **significance** is omitted, the function defaults to rounding to the nearest integer (`significance = 1`).
- This function has consistent behavior for both positive and negative numbers. For example, rounding `7.8` or `-7.8`
  with the same **significance** produces results in opposite directions but consistent with the absolute rounding
  logic.
- The `FLOOR.PRECISE` function is highly valuable for financial or numeric analysis where uniform handling of positive
  and negative values is critical.