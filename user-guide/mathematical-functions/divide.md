<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## "/" Operator

In Excel, the `/` symbol is used as an arithmetic operator to divide one number by another.

### Usage:

You can use the `/` operator to divide numbers, cell references, ranges, or even the results of other functions.

### Examples:

1. `=10 / 2` would return 5.
2. `=B1 / A1` would divide the value in cell B1 by the value in cell A1.
3. `=100 / SUM(A1:A10)` would divide 100 by the sum of the numbers in cells A1 through A10.

When using the `/` operator, it's essential to ensure that the cells or ranges you're dividing contain numerical values. If a cell contains text or is empty, Excel will treat that cell's value as 0. Notably, if you divide by zero (e.g., `10 / 0` or `A1 / B1` where B1 has a value of 0), you'll get a `#DIV/0!` error, indicating an undefined division.