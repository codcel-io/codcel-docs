<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COUNTIFS Function

The `COUNTIFS` function in Excel is used to count the number of cells that meet multiple criteria across one or more
ranges. It is an extension of the `COUNTIF` function, which handles a single condition, whereas `COUNTIFS` allows for
more complex filtering with multiple conditions.

### Key Features of COUNTIFS:

- Evaluates multiple criteria for a single range or multiple ranges.
- Returns the count of rows or columns where all specified criteria are met.
- Criteria can include logical comparisons, specific text, numbers, or even wildcards (e.g., `*` or `?` for partial text
  matches).

### Syntax:

```plaintext
COUNTIFS(criteria_range1, criteria1, [criteria_range2, criteria2], ...)
```

- **criteria_range1**: The first range of cells to evaluate.
- **criteria1**: The condition to apply to `criteria_range1`.
- **[criteria_range2, criteria2]** *(optional)*: Additional ranges and their corresponding conditions.

### Examples:

1. **Simple Count with One Range and Condition**  
   `=COUNTIFS(A1:A10, ">50")`  
   Counts cells in the range `A1:A10` where values are greater than 50.  
   **Result**: The count of cells fulfilling this condition.

2. **Multiple Ranges and Criteria**  
   `=COUNTIFS(A1:A10, ">50", B1:B10, "<100")`  
   Counts rows where the value in `A1:A10` is greater than 50 *and* the value in `B1:B10` is less than 100.  
   **Result**: The number of rows where both conditions are true.

3. **Using Text as Criteria**  
   `=COUNTIFS(A1:A10, "Apples")`  
   Counts the number of cells in `A1:A10` that contain the text `"Apples"`.  
   **Result**: A count of cells matching the exact text.

4. **Using Wildcards**  
   `=COUNTIFS(A1:A10, "Apple*")`  
   Counts how many cells in `A1:A10` start with `"Apple"`. The `*` wildcard matches any number of trailing characters.  
   **Result**: A count of cells matching the pattern.

5. **Case with Dates**  
   `=COUNTIFS(A1:A10, ">=01/01/2023", A1:A10, "<=12/31/2023")`  
   Counts how many cells in the range `A1:A10` contain dates in the year 2023.  
   **Result**: The number of dates within the specified range.

### Notes:

- All criteria ranges must have the same size, or Excel will return a `#VALUE!` error.
- `COUNTIFS` supports logical operators (e.g., `>`, `<`, `=`, `>=`, `<=`).
- If no cells meet the specified criteria, the result will be `0`.
- Use `COUNTIFS` to filter and count data based on multiple dynamic conditions, making it ideal for advanced data
  analysis.

> **Tip**: Use `COUNTIFS` to count data based on multiple filters, such as combining conditions for numbers, dates, and
text for precise results in large datasets.