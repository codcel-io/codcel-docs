<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COUNT Function

The `COUNT` function in Excel is used to count the number of numeric values in a range or list of arguments. It is
particularly useful when you want to determine how many cells in a specified range contain numbers.

### Key Features of COUNT:

- Counts only numeric values (including integers, decimals, and dates).
- Ignores empty cells, text, and logical values (e.g., `TRUE`, `FALSE`) unless entered as direct arguments.
- Frequently used for data analysis to understand the size of a dataset with numeric entries.

### Syntax:

```plaintext
COUNT(value1, [value2], ...)
```

- **value1**: The first range, cell, or value to count.
- **[value2]** *(optional)*: Additional values, ranges, or cells to include in the count.

### Examples:

1. `=COUNT(A1:A10)`  
   Counts the number of numeric values in the range `A1:A10`.  
   **Result**: A numeric value representing the count of numbers within that range.

2. `=COUNT(5, "Text", TRUE, 10)`  
   Counts numeric values from a list of arguments.  
   **Result**: `2`, as only `5` and `10` are numeric.

3. `=COUNT(A1:A10, B1:B10)`  
   Counts numeric values across two ranges: `A1:A10` and `B1:B10`.  
   **Result**: A single numeric value based on the total numbers in both ranges.

### Notes:

- Any logical values such as `TRUE` or `FALSE` and text are ignored unless directly passed as arguments.
- If no numeric values are found in the specified range(s), the result will be `0`.
- To count non-numeric values (e.g., logical values, text, or errors), consider using the `COUNTA` function.

> **Tip**: Use the `COUNT` function to quickly find the number of numeric entries in your dataset, especially when
working with calculations or summaries.