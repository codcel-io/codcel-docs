<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## AVERAGEIFS Function

The `AVERAGEIFS` function in Excel calculates the **arithmetic mean** (average) of all cells in a range that meet
multiple specified criteria. This function is particularly useful for finding the average of a subset of data that
matches specific conditions.

### Syntax:

    AVERAGEIFS(average_range, criteria_range1, criteria1, [criteria_range2, criteria2], ...)

- **average_range**: The range of cells to calculate the average from. These are the numbers for which you want to
  compute the average.
- **criteria_range1**: The range of cells to evaluate against the first condition.
- **criteria1**: The condition or criteria used to define which values in `criteria_range1` are included in the
  calculation.
- **[criteria_range2, criteria2], ...**: Optional additional ranges and their respective conditions. You can specify up
  to 127 conditions.

### Key Points:

- All ranges (e.g., `average_range`, `criteria_range1`, etc.) must be the same size; otherwise, the function will return
  an error.
- Criteria can include logical operators (`>`, `<`, `>=`, `<=`, `=`, `<>`) and wildcards (`*`, `?`) for text-based
  conditions:
    - `*` matches any sequence of characters.
    - `?` matches a single character.
- If no cells meet the criteria, `AVERAGEIFS` will return the `#DIV/0!` error.
- Logical values like `TRUE` and `FALSE` are treated as numeric values (TRUE = `1`, FALSE = `0`) if used in the ranges.

### Examples:

1. **Basic Usage:**
   ```excel
   =AVERAGEIFS(A1:A10, B1:B10, ">5")
   ```
   Calculates the average of cells in the range `A1:A10` where the corresponding cells in `B1:B10` are greater than `5`.

2. **Multiple Criteria:**
   ```excel
   =AVERAGEIFS(A1:A10, B1:B10, ">5", C1:C10, "<20")
   ```
   Averages cells in `A1:A10` where values in `B1:B10` are greater than `5` and values in `C1:C10` are less than `20`.

3. **Using Wildcards for Text Criteria:**
   ```excel
   =AVERAGEIFS(A1:A10, B1:B10, "John*", C1:C10, ">=100")
   ```
   Calculates the average of cells in `A1:A10` where:
    - `B1:B10` contains text starting with "John",
    - `C1:C10` contains values greater than or equal to `100`.

4. **Criteria with Dates:**
   ```excel
   =AVERAGEIFS(A1:A10, B1:B10, ">=01/01/2023", B1:B10, "<01/01/2024")
   ```
   Averages cells in `A1:A10` where the corresponding dates in `B1:B10` fall within the year 2023.

### Notes:

- The `AVERAGEIFS` function is an extension of `AVERAGEIF`, allowing for multiple criteria instead of just one.
- Unlike `SUMIFS` or `COUNTIFS`, the `AVERAGEIFS` function focuses on returning an average instead of a sum or count.
- Make sure all ranges provided have the same number of rows and columns; otherwise, you will encounter a `#VALUE!`
  error.

> **Tip**: Use `AVERAGEIFS` to generate advanced statistical insights, such as filtering data by conditions before
> calculating averages. It is a versatile function for handling conditional averaging in data analysis.