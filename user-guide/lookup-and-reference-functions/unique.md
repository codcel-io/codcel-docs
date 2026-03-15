<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## UNIQUE Function

Introduced in Excel for Microsoft 365 and Excel 2019, the `UNIQUE` function extracts unique values from a range or array. It's useful for removing duplicates and getting a list of distinct values.

### Syntax:

    UNIQUE(array, [by_col], [exactly_once])

- **array**: The range or array from which you want to extract unique values.
- **by_col** (optional): A logical value (TRUE or FALSE) that determines how to compare;
    - If `TRUE`, the function searches for unique values based on columns.
    - If `FALSE` or omitted, it searches for unique values based on rows.
- **exactly_once** (optional): Another logical value (TRUE or FALSE);
    - If `TRUE`, the function returns only values that appear exactly once.
    - If `FALSE` or omitted, it returns all unique values, regardless of how many times they appear.

### Examples:

1. `=UNIQUE(A1:A10)` would return a list of unique values from the range `A1:A10`.
2. `=UNIQUE(B1:D1, TRUE)` would return unique values from the first row of `B1:D1`, comparing across columns.
3. `=UNIQUE(A1:C3, FALSE, TRUE)` would extract values that occur exactly once in the range `A1:C3`, comparing across rows.

### Usage Notes:
- The `UNIQUE` function is particularly powerful for data analysis, allowing quick extraction of distinct values from a dataset.
- It can be combined with other functions like `SORT` to further manipulate the list of unique values.
- The function automatically spills the results into adjacent cells (known as a dynamic array) if using a version of Excel that supports dynamic arrays.

> **Note**: by_col NEEDS TO BE TESTED IN Codcel.

> **Note**: The `UNIQUE` function is only available in Excel for Microsoft 365 and Excel 2019. If you're using an older version, you might need to use a combination of other functions, like `IF` and `FREQUENCY`, or use features like Conditional Formatting and PivotTables to extract unique values.