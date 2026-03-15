<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## EVEN Function

The `EVEN` function in Excel rounds a number up to the nearest even integer. If the number is already an even integer, it remains the same.

### Syntax:

    EVEN(number)


- **number**: The value you want to round.

### Examples:
1. `=EVEN(3)` will return `4` because 4 is the nearest even integer greater than 3.
2. `=EVEN(2)` will return `2` because 2 is already an even integer.
3. `=EVEN(-3)` will return `-4`. Note that for negative numbers, the function still rounds away from zero.

### Usage Notes:
- This function is particularly useful in scenarios where you need to ensure that a number is even, such as when aligning items in a grid or matching pairs.
- If you need to round a number up to the nearest odd integer, you can use the `ODD` function.

> **Important**: The `EVEN` function behaves differently with positive and negative numbers. For positive numbers, it rounds up to the nearest even integer, while for negative numbers, it rounds down (away from zero) to the nearest even integer.