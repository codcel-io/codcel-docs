<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COUNTIF Function

The `COUNTIF` function in Excel is used to count the number of cells within a range that meet a single specified criterion. This function is useful for a variety of data analysis tasks where you need to count items based on specific conditions.

### Syntax:

    COUNTIF(range, criteria)

- **range**: The range of cells you want to apply the criteria to.
- **criteria**: The condition that will determine which cells to count. This can be a number, expression, cell reference, or text that defines which cells will be counted.

### Examples:

1. `=COUNTIF(A1:A10, ">5")` would count the number of cells in the range `A1:A10` that contain numbers greater than 5.
2. `=COUNTIF(B1:B10, "Bananas")` would count all the cells in `B1:B10` that contain the exact word "Bananas".
3. `=COUNTIF(C1:C10, D1)` would count all the cells in `C1:C10` that match the content of cell `D1`.

### Usage Notes:
- The `criteria` can include wildcards such as `?` (to represent any single character) and `*` (to represent any sequence of characters) when you want to match patterns.
- `COUNTIF` is case-insensitive, meaning it treats uppercase and lowercase letters as the same.
- The function can be used for both numeric and text data, as well as for more complex criteria involving text strings, dates, and functions.

> **Note**: For criteria that involve multiple conditions across different ranges, you would use the `COUNTIFS` function, which is the plural version capable of handling multiple criteria.