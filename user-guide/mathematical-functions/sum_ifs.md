<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUMIFS Function

The `SUMIFS` function in Excel sums the values in a range based on multiple criteria. It's a powerful tool for
aggregating data when you have more than one condition to meet.

### Syntax:

    SUMIFS(sum_range, criteria_range1, criteria1, [criteria_range2, criteria2], ...)

- **sum_range**: The range of cells to be added if the conditions are met.
- **criteria_range1**: The first range of cells to evaluate against the first condition (`criteria1`).
- **criteria1**: The condition applied to `criteria_range1`. This can be a number, expression, cell reference, or text.
- **criteria_range2, criteria2, ...** (optional): Additional ranges and their corresponding conditions. Each range is
  evaluated with its respective condition.

### Examples:

1. `=SUMIFS(B1:B10, A1:A10, ">20")`  
   Sums the values in `B1:B10` where the corresponding cells in `A1:A10` are greater than 20.

2. `=SUMIFS(C1:C10, A1:A10, ">=10", B1:B10, "<5")`  
   Sums the values in `C1:C10` where the corresponding cells in `A1:A10` are greater than or equal to 10 **and** the
   corresponding cells in `B1:B10` are less than 5.

3. `=SUMIFS(D1:D10, B1:B10, "Apples", C1:C10, "Red")`  
   Sums the values in `D1:D10` where the corresponding cells in `B1:B10` contain "Apples" **and** the corresponding
   cells in `C1:C10` contain "Red".

### Usage Notes:

- All ranges (`sum_range`, `criteria_range1`, `criteria_range2`, etc.) must have the **same size and shape**, or Excel
  will return an error.
- The function works with **logical conditions** (e.g., `>`, `<`, `=`) and supports wildcards (`*` and `?`) for text
  conditions.
    - `*` matches any sequence of characters.
    - `?` matches a single character.
- `SUMIFS` supports multiple conditions joined with an implicit "AND." For conditions joined with "OR," you may need to
  use separate `SUMIFS` functions combined with `+`.

> **Note**: Ensure your data is consistent and ranges are properly aligned for accurate results.