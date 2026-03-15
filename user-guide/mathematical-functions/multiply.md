<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## "*" Operator

In Excel, the `*` symbol is used as an arithmetic operator to multiply numbers together.

### Usage:

You can use the `*` operator to multiply numbers, cell references, ranges, or even the results of other functions.

### Examples:

1. `=5 * 10` would return 50.
2. `=A1 * B1` would multiply the values in cells A1 and B1.
3. `=SUM(A1:A10) * 2` would sum the numbers in cells A1 through A10 and then multiply the result by 2.

Ensure the cells or ranges you're multiplying with the `*` operator contain numerical values. If a cell contains text or is empty, Excel will treat that cell's value as 0 in the multiplication operation. However, if you directly attempt multiplication with a text value (e.g., `="text" * 5`), you'll get an error.