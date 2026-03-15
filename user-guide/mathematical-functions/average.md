<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## AVERAGE Function

The `AVERAGE` function in Excel calculates the arithmetic mean of a group of numbers. This function adds up all the numbers in the specified range and then divides by the count of those numbers.

### Syntax:

    AVERAGE(number1, [number2], ...)


- **number1**: The first number or range for which you want to find the average.
- **number2** (optional): Additional numbers or ranges you want to include in the average. You can specify up to 255 numbers or ranges.

### Examples:

1. `=AVERAGE(1, 2, 3, 4, 5)` would return `3`, as the sum of these numbers is 15 and there are 5 numbers, resulting in an average of 15/5.
2. `=AVERAGE(A1:A5)` would return the average of the values contained in cells A1 through A5.
3. `=AVERAGE(A1:A5, C1:C3)` would compute the average of the values in cells A1 through A5 and C1 through C3 combined.

> **Note**: The `AVERAGE` function ignores cells that are empty, cells containing text, and cells with error values. However, it does consider cells with zero (0) in its calculations.