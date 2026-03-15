<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## AVERAGEIF Function

The `AVERAGEIF` function in Excel calculates the **average (arithmetic mean)** of all the cells that meet a specified
condition (criteria) within a given range.

### Key Features of AVERAGEIF:

- Averages only those numbers in a range that satisfy a specific condition or criteria.
- Supports conditions with numeric values, text, or operators (e.g., `>`, `<`, `=`).
- Optionally allows defining a separate range for average calculation.

This function is useful for calculating averages dynamically based on specific rules or conditions.

### Syntax:

```plaintext
AVERAGEIF(range, criteria, [average_range])
```

- **range**: *(Required)* The range of cells to be evaluated using the criterion.
- **criteria**: *(Required)* The condition that determines which cells are included in the average.
    - Can be a number (e.g., `10`), expression (e.g., `">5"`), text (e.g., `"apples"`), or reference to a cell
      containing the condition.
- **average_range**: *(Optional)* The range of cells to be averaged. If omitted, `range` is used.

### Examples:

1. **Basic Usage**
   ```plaintext
   =AVERAGEIF(A1:A10, ">5")
   ```
   Averages all numbers in the range `A1:A10` that are greater than 5.

2. **Using Text as Criteria**
   ```plaintext
   =AVERAGEIF(B1:B10, "Apples")
   ```
   Calculates the average of cells in `B1:B10` where the values equal "Apples".

3. **With Separate Average Range**
   ```plaintext
   =AVERAGEIF(A1:A10, ">5", B1:B10)
   ```
   Averages values in the range `B1:B10` where the corresponding values in `A1:A10` are greater than 5.

4. **Using Cell Reference for Criteria**
   ```plaintext
   =AVERAGEIF(A1:A10, C1)
   ```
   Uses the value or condition stored in cell `C1` as the criterion.

5. **With Wildcards**
   ```plaintext
   =AVERAGEIF(A1:A10, "Ap*")
   ```
   Averages values in `A1:A10` where the text starts with "Ap" (e.g., "Apple", "Apricot"). The `*` wildcard represents
   any number of characters.

### Notes:

- **Wildcards**: The `?` and `*` wildcards can be used in the `criteria` for matching text:
    - `?` matches any single character.
    - `*` matches any number of characters.
    - To use literal `?` or `*`, place a tilde (`~`) before them (e.g., `"a~*"` matches "a*").
- **Empty Criteria**: If `average_range` has numeric and non-numeric values, only numeric ones are averaged.
- **Errors**: If no cells meet the criteria or the range is empty, the function will return a `#DIV/0!` error.

> **Tip**: Use `AVERAGEIF` when you need conditional averages and precise control over what gets factored into your
calculations.