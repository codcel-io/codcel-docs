<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COVAR Function

The `COVAR` function in Excel is used to calculate the covariance of two data sets. Covariance is a measure of the
linear relationship between two variables. It helps to understand how changes in one variable are associated with
changes in another variable.

### Key Features of COVAR:

- Calculates the **average of the product of deviations** of paired data points from their respective means.
- Indicates the **direction** of the relationship between two variables:
    - Positive covariance: Both variables tend to move in the same direction.
    - Negative covariance: Variables tend to move in opposite directions.
- Useful in **statistics** and **finance**, especially in understanding relationships between variables.

### Syntax:

```plaintext
COVAR(array1, array2)
```

- **array1**: The first range of numeric data.
- **array2**: The second range of numeric data.

### Examples:

1. `=COVAR(A1:A5, B1:B5)`  
   Calculates the covariance between the data sets in the ranges `A1:A5` (first data set) and `B1:B5` (second data
   set).  
   **Result**: A positive, negative, or zero value depending on the relationship between the two data sets.

2. `=COVAR({1, 2, 3}, {4, 5, 6})`  
   Returns the covariance of the two arrays `{1, 2, 3}` and `{4, 5, 6}`.  
   **Result**: Positive covariance (as both arrays increase together).

### Notes:

- **Array Length**: The arrays `array1` and `array2` must have the same number of data points and cannot be empty, or
  the function will return a `#N/A` error.
- **Numeric Values Only**: If any cell in the arrays contains non-numeric data, the `COVAR` function will ignore it.
- If array1 and array2 contain only one data point each, the function will return a `#DIV/0!` error because the division
  by zero is not defined.

### Formula Behind COVAR:

The covariance is calculated using the formula:

```plaintext
COVAR = Σ((x - x̄) * (y - ӯ)) / n
```

Where:

- `x` and `y`: The data points in `array1` and `array2`.
- `x̄` and `ӯ`: The means of `array1` and `array2`, respectively.
- `n`: The number of data points in the arrays.

### Use Cases:

- **Finance**: Calculate the covariance between two stock prices to understand how they move together.
- **Statistics**: Assess the relationship between two variables in experiments or observations.
- **Portfolio Management**: Use covariance to determine the correlation and diversification of assets in an investment
  portfolio.

> **Tip**: For newer Excel versions, use the `COVARIANCE.P` or `COVARIANCE.S` functions for population or sample
> covariance, respectively, as they are more precise.