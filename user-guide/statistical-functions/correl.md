<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CORREL Function

The `CORREL` function in Excel calculates the **correlation coefficient** between two data sets. The correlation
coefficient measures the statistical relationship between two variables, indicating how changes in one variable are
associated with changes in the other.

It is commonly used in statistical analysis to determine the strength and direction of a linear relationship between two
sets of data.

### Key Features of CORREL:

- Calculates the Pearson correlation coefficient for two data arrays.
- Measures the direction and strength of a linear relationship between two variables:
    - A value close to `1` indicates a strong positive correlation.
    - A value close to `-1` indicates a strong negative correlation.
    - A value close to `0` indicates no linear correlation.
- Useful in various fields such as data analysis, finance, and research to understand relationships between variables.

### Syntax:

```plaintext
CORREL(array1, array2)
```

- **array1**: The first array or range of data points.
- **array2**: The second array or range of data points. Must have the same number of data points as `array1`.

### Examples:

1. `=CORREL(A1:A10, B1:B10)`  
   Calculates the correlation coefficient between the values in the ranges `A1:A10` and `B1:B10`.  
   **Result**: A single value between `-1` and `1`, representing the correlation.

2. `=CORREL({1, 2, 3}, {12, 14, 16})`  
   Finds the correlation coefficient for two arrays: `{1, 2, 3}` and `{12, 14, 16}`.  
   **Result**: `1`, indicating a perfect positive linear relationship.

3. `=CORREL(A1:A10, C1:C10)`  
   Computes the correlation coefficient for values in `A1:A10` and `C1:C10`.  
   **Result**: A value based on the relationship between these data points.

### Notes:

- If the arrays have different numbers of data points or are empty, the function returns an error (`#N/A`).
- The formula assumes that both data sets are numeric. Non-numeric values are ignored.
- The closer the value is to `1` or `-1`, the stronger the linear relationship. A value near `0` suggests no linear
  relationship.
- This function is limited to linear correlations and may not accurately measure nonlinear relationships.

> **Tip**: Use the `CORREL` function to quickly estimate the relationship between two sets of data in your analysis
workflows.