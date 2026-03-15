<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COUNTBLANK Function

The `COUNTBLANK` function in Excel is used to count the number of empty (blank) cells in a specified range. It is
particularly useful when you want to identify missing data or gaps in a dataset.

### Key Features of COUNTBLANK:

- Counts only empty cells within the specified range.
- Cells containing formulas that return empty strings (`""`) are counted as blank.
- Cells containing zero (`0`), text, errors, or logical values are **not** counted as blank.
- Frequently used for data validation and quality checks to find missing entries.

### Syntax:

```plaintext
COUNTBLANK(range)
```

- **range**: The range of cells in which you want to count blank cells.

### Examples:

1. `=COUNTBLANK(A1:A10)`
   Counts the number of empty cells in the range `A1:A10`.
   **Result**: A numeric value representing the count of blank cells within that range.

2. `=COUNTBLANK(A1:C10)`
   Counts the number of empty cells across a multi-column range from `A1` to `C10`.
   **Result**: The total number of blank cells in the entire range.

3. `=COUNTBLANK(B2:B100)`
   Counts blank cells in a single column range, useful for checking how many entries are missing in a data column.
   **Result**: The count of blank cells in `B2:B100`.

### Notes:

- Cells that contain formulas returning an empty string (`=""`) are treated as blank and will be counted.
- Cells containing a space character (`" "`) are **not** considered blank.
- If no cells in the range are blank, the result will be `0`.
- To count non-empty cells, consider using the `COUNTA` function. To check if an individual cell is blank, use the `ISBLANK` function.

> **Tip**: Use the `COUNTBLANK` function to quickly audit your data for missing values, especially before running
calculations or creating summaries that require complete datasets.