<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUMX2PY2 Function

The `SUMX2PY2` function in Excel calculates the sum of the sum of the squares of corresponding values in two arrays. It
is useful in mathematical or statistical operations where you analyze or combine squared values.

### Syntax:

    SUMX2PY2(array_x, array_y)

- **array_x**: The first array or range of numeric values to be squared.
- **array_y**: The second array or range of numeric values to be squared and added together with the first.

### Key Behaviors:

1. Each value in `array_x` is squared.
2. Each value in `array_y` is squared.
3. The squared values of `array_x` and the squared values of `array_y` are added together for each corresponding pair.
4. The resulting sums are summed.

- The function requires both arrays to have the **same number of elements**. If not, it returns a `#VALUE!` error.
- Non-numeric values are ignored (treated as zero).
- Logical values (`TRUE`, `FALSE`) in the arrays are handled as:
    - `TRUE = 1` and `FALSE = 0`.

### Examples:

1. `=SUMX2PY2({2, 3}, {1, 2})`  
   Calculates:  
   \( (2^2 + 1^2) + (3^2 + 2^2) = (4 + 1) + (9 + 4) = 5 + 13 = 18 \)

2. `=SUMX2PY2(A1:A3, B1:B3)`  
   If `A1:A3` contains `{4, 5, 6}` and `B1:B3` contains `{1, 2, 3}`, the calculation is:  
   \( (4^2 + 1^2) + (5^2 + 2^2) + (6^2 + 3^2) = (16 + 1) + (25 + 4) + (36 + 9) = 17 + 29 + 45 = 91 \)

3. `=SUMX2PY2({2, 1, TRUE}, {1, 0, FALSE})`  
   Logical values are treated as numbers:  
   \( (2^2 + 1^2) + (1^2 + 0^2) + (1^2 + 0^2) = (4 + 1) + (1 + 0) + (1 + 0) = 5 + 1 + 1 = 7 \)

4. **Error Example**:  
   If `A1:A3` contains `{2, 3}` and `B1:B4` contains `{1, 2, 3, 4}`, `=SUMX2PY2(A1:A3, B1:B4)` returns **`#VALUE!`**  
   This happens because the number of elements in the two arrays is not equal.

### Usage Notes:

- The `SUMX2PY2` function is particularly helpful in paired data analysis, such as analyzing the sum of quadratic
  transformations of two datasets.
- Ensure that the two arrays (or ranges) are the same size to avoid errors.
- Can be combined with other mathematical or statistical functions for more complex calculations.

> **Tip**: Use this function to efficiently calculate sums of combined squared terms for arrays or paired data analysis.