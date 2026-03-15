<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MAX Function

The `MAX` function in Excel is used to return the largest value from a set of values.

### Syntax:

    MAX(number1, [number2], ...)

- **number1**: This is a required argument. It can be a number, a range of numbers, or a reference to a cell containing a number.
- **[number2], ...**: These are optional arguments. Like `number1`, they can be numbers, ranges, or cell references. You can input multiple numbers or ranges.

### Examples:

1. `=MAX(A1:A10)` would return the largest number in cells A1 through A10.
2. `=MAX(A1, B1, C1)` would return the largest number among cells A1, B1, and C1.
3. `=MAX(5, 10, 15)` would return 15.

If a cell within the range of values you're evaluating with `MAX` contains text or is empty, Excel simply ignores that cell when determining the maximum value. If all the cells in the specified range contain text or are empty, the `MAX` function will return 0.