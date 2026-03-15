<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COVARIANCE.S Function

The `COVARIANCE.S` function in Excel calculates the **sample covariance** between two data sets. Covariance measures how
two data sets vary together. Specifically, it indicates whether an increase in one variable relates to an increase or
decrease in another variable.

This function is commonly used in statistics, finance, and data analysis to evaluate relationships between sample data
sets, such as stock return trends or experimental measurements.

### Key Features of COVARIANCE.S:

- Calculates the sample covariance between two arrays of data.
- Provides insights into the direction of the relationship between two variables:
    - A **positive covariance** suggests that as one variable increases, the other tends to increase as well.
    - A **negative covariance** suggests that as one variable increases, the other tends to decrease.
- Used when working with sample data instead of the entire population.

### Syntax:

```plaintext
COVARIANCE.S(array1, array2)
```

- **array1**: The first array or range of numeric data points.
- **array2**: The second array or range of numeric data points. Must have the same number of data points as `array1`.

### Examples:

1. `=COVARIANCE.S(A1:A10, B1:B10)`  
   Calculates the sample covariance between the values in the ranges `A1:A10` and `B1:B10`.  
   **Result**: A single numeric value representing the sample covariance.

2. `=COVARIANCE.S({1, 2, 3}, {4, 5, 6})`  
   Computes the sample covariance for two arrays: `{1, 2, 3}` and `{4, 5, 6}`.  
   **Result**: `1.0`, indicating a positive relationship.

3. `=COVARIANCE.S(A1:A5, C1:C5)`  
   Calculates the sample covariance of values in the ranges `A1:A5` and `C1:C5`.  
   **Result**: A numeric value indicating how the two sample data sets vary together.

### Notes:

- If the arrays have different numbers of data points or are empty, the function returns an error (`#N/A`).
- Non-numeric values in the arrays are ignored.
- The size of the covariance does **not** directly indicate the strength of the relationship because it depends on the
  scale of the variables. For a normalized measure, use the `CORREL` function to compute the correlation coefficient.
- The function assumes that the input data represents a **sample**, not an entire population. For population covariance,
  use the `COVARIANCE.P` function.

> **Tip**: Use the `COVARIANCE.S` function to analyze sample data sets and uncover the relationship between variables
> for informed decision-making in statistical, financial, and experimental domains.