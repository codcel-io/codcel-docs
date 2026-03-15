<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUMXMY2 Function

The `SUMXMY2` function in Excel calculates the sum of the squares of differences between corresponding values in two
arrays. It is commonly used in mathematical or statistical operations where you analyze squared deviations.

### Syntax:

    SUMXMY2(array_x, array_y)

- **array_x**: The first array or range of numeric values.
- **array_y**: The second array or range of numeric values to be subtracted from the first.

### Key Behaviors:

1. Each value in `array_x` is paired with the corresponding value in `array_y`.
2. The difference between each pair (`array_x - array_y`) is calculated.
3. Each difference is squared.
4. The resulting squared differences are summed up.

- The function requires both arrays to have the **same number of elements**. If not, it returns a `#VALUE!` error.
- Non-numeric values are ignored (treated as zero).
- Logical values (`TRUE`, `FALSE`) in the arrays are handled as:
    - `TRUE = 1` and `FALSE = 0`.

### Examples:

1. `=SUMXMY2({2, 3}, {1, 2})`  
   Calculates:  
   \( (2 - 1)^2 + (3 - 2)^2 = 1^2 + 1^2 = 1 + 1 = 2 \)

2. `=SUMXMY2(A1:A3, B1:B3)`  
   If `A1:A3` contains `{4, 5, 6}` and `B1:B3` contains `{1, 2, 3}`, the calculation is:  
   \( (4 - 1)^2 + (5 - 2)^2 + (6 - 3)^2 = 3^2 + 3^2 + 3^2 = 9 + 9 + 9 = 27 \)

3. `=SUMXMY2({2, 1, TRUE}, {1, 0, FALSE})`  
   Logical values are treated as numbers:  
   \( (2 - 1)^2 + (1 - 0)^2 + (1 - 0)^2 = 1^2 + 1^2 + 1^2 = 1 + 1 + 1 = 3 \)

4. **Error Example**:  
   If `A1:A2` contains `{2, 3}` and `B1:B3` contains `{1, 2, 3}`, `=SUMXMY2(A1:A2, B1:B3)` returns **`#VALUE!`**  
   This happens because the number of elements in the two arrays is not equal.

### Usage Notes:

- The `SUMXMY2` function is useful in statistical and paired data analysis where you need to measure squared differences
  between two datasets.
- Ensure that the two arrays (or ranges) are the same size to avoid errors.
- Can be combined with other Excel functions to perform more complex operations.

> **Tip**: Use this function for analyzing deviations between paired data points and calculating sums of squared
differences efficiently.