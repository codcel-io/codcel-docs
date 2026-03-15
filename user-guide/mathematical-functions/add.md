<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## "+" Operator

In Excel, the `+` symbol is used as an arithmetic operator to add numbers together.

### Usage:

You can use the `+` operator to add numbers, cell references, ranges, or even the results of other functions.

### Examples:

1. `=5 + 10` would return 15.
2. `=A1 + B1` would add the values in cells A1 and B1.
3. `=SUM(A1:A10) + 100` would sum the numbers in cells A1 through A10 and then add 100 to the result.

It's crucial to ensure the cells or ranges you're trying to add with the `+` operator contain numerical values. If a cell contains text or is empty, Excel will treat that cell's value as 0 in the addition operation. However, if you directly try to add a text value (like `="text" + 5`), 
you'll get an error.

> **Note**: While the `+` operator can add two numbers or cell references, if you want to sum a range of cells, functions like `SUM` are more appropriate and versatile.