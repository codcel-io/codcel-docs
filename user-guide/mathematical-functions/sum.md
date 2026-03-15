<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUM Function

The `SUM` function in Excel is used to add together the values in a range of cells. It is one of the most commonly used functions in Excel for performing arithmetic operations.

### Syntax:

    SUM(number1, [number2], ...)

- **number1**: This is a required argument. It can be a number, a range of numbers, or even a reference to a cell containing a number.
- **[number2], ...**: These are optional arguments. Like `number1`, they can be numbers, ranges, or cell references. You can input up to 255 numbers as separate arguments.

### Examples:

1. `=SUM(A1:A10)` would sum all the numbers in cells A1 through A10.
2. `=SUM(A1, B1, C1)` would sum the numbers in cells A1, B1, and C1.
3. `=SUM(5, 10, 15)` would return 30.

If a cell within the range of cells you're trying to sum contains text or is empty, Excel simply ignores that cell when performing the addition. If all the cells in the specified range contain text or are empty, the `SUM` function will return 0.