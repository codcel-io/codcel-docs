<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUMIF Function

The `SUMIF` function in Excel sums the values in a range that meet specified criteria. It's particularly useful for adding up numbers in a range where certain conditions are met.

### Syntax:

    SUMIF(range, criteria, [sum_range])

- **range**: The range of cells you want evaluated by your criterion.
- **criteria**: The condition that determines which cells will be added. This can be a number, expression, cell reference, or text that defines which cells will be summed.
- **sum_range** (optional): The actual cells to sum if they meet the criteria in `range`. If omitted, Excel sums the cells in `range` that meet the criteria.

### Examples:

1. `=SUMIF(A1:A10, ">20")` would sum all numbers in the range `A1:A10` that are greater than 20.
2. `=SUMIF(B1:B10, "Apples", C1:C10)` would sum all the values in `C1:C10` where the corresponding cells in `B1:B10` contain the word "Apples".
3. `=SUMIF(A1:A10, D1, B1:B10)` would sum all the values in `B1:B10` where the corresponding cells in `A1:A10` match the value in `D1`.

### Usage Notes:
- `SUMIF` can be used for basic conditions, such as summing values that are greater than, less than, equal to, or not equal to a specified value.
- It's important to ensure that `range` and `sum_range` are of the same size and shape, otherwise, the function may return unexpected results.

> **Note**: For more complex conditions involving multiple criteria, the `SUMIFS` function (which handles multiple criteria) can be used.