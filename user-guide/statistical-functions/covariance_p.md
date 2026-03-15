<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COVARIANCE.P Function

The `COVARIANCE.P` function in Excel calculates the **population covariance** between two data sets. Covariance is a
measure of how two data sets vary together. Specifically, it indicates whether an increase in one variable generally
corresponds to an increase or decrease in another variable.

It is commonly used in statistical analysis, especially in finance and investment, to analyze relationships between
variables such as stock returns.

### Key Features of COVARIANCE.P:

- Calculates the population covariance between two arrays of data.
- Indicates the direction of the relationship between two variables:
    - A **positive covariance** suggests that as one variable increases, the other tends to increase as well.
    - A **negative covariance** suggests that as one variable increases, the other tends to decrease.
- Helps in analyzing dependencies and relationships between data sets.

### Syntax:

```plaintext
COVARIANCE.P(array1, array2)
```

- **array1**: The first array or range of numeric data points.
- **array2**: The second array or range of numeric data points. Must have the same number of data points as `array1`.

### Examples:

1. `=COVARIANCE.P(A1:A10, B1:B10)`  
   Calculates the population covariance between the values in the ranges `A1:A10` and `B1:B10`.  
   **Result**: A single numeric value representing the population covariance.

2. `=COVARIANCE.P({1, 2, 3}, {4, 5, 6})`  
   Computes the population covariance for two arrays: `{1, 2, 3}` and `{4, 5, 6}`.  
   **Result**: `0.6667`, indicating a positive relationship.

3. `=COVARIANCE.P(A1:A5, C1:C5)`  
   Calculates the population covariance for values in `A1:A5` and `C1:C5`.  
   **Result**: A numeric value based on how the data sets vary together.

### Notes:

- If the arrays have different numbers of data points or are empty, the function returns an error (`#N/A`).
- Only numeric values are considered. Non-numeric values in the arrays are ignored.
- The size of the covariance does not directly indicate the strength of a relationship, as it depends on the scale of
  the variables. Use the `CORREL` function to calculate a normalized correlation coefficient.
- This function assumes that the input data represents the entire population. For a sample covariance, use the
  `COVARIANCE.S` function instead.

> **Tip**: Use the `COVARIANCE.P` function in statistical and financial analyses to understand how two variables are
related in terms of their population behavior.