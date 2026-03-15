<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## "-" Operator

In Excel, the `-` symbol is utilized as an arithmetic operator to perform subtraction operations between numbers.

### Usage:

You can use the `-` operator to subtract numbers, cell references, ranges, or even the results of other functions.

### Examples:

1. `=10 - 5` would return 5.
2. `=B1 - A1` would subtract the value in cell A1 from the value in cell B1.
3. `=100 - SUM(A1:A10)` would subtract the sum of the numbers in cells A1 through A10 from 100.

It's essential to ensure that the cells or ranges you're using with the `-` operator contain numerical values. If a cell has text or is empty, Excel will treat that cell's value as 0 in the subtraction operation. However, if you directly try to subtract using a text value (e.g., `="text" - 5`), you'll encounter an error.