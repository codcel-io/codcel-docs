<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHIINV Function

The `CHIINV` function in Excel returns the inverse of the right-tailed probability of the chi-squared distribution. It
is commonly used to determine the chi-squared critical value for a given probability and degrees of freedom, which is
useful in hypothesis testing and confidence interval calculations.

### Key Features of CHIINV:

- Computes the **chi-squared value** corresponding to a specific right-tailed probability.
- Commonly used in **goodness-of-fit tests** and **independence tests**.
- Allows determination of critical chi-squared values for testing statistical significance.

### Syntax:

```plaintext
CHIINV(probability, degrees_freedom)
```

- **probability**: The probability corresponding to the right tail of the chi-squared distribution (must be between 0
  and 1).
- **degrees_freedom**: The number of degrees of freedom for the distribution (must be ≥ 1).

### Examples:

1. `=CHIINV(0.05, 10)`  
   Returns the chi-squared value for a right-tailed probability of `0.05` (5%) with `10` degrees of freedom.  
   **Result**: 18.307

2. `=CHIINV(0.01, 5)`  
   Calculates the chi-squared value for a right-tailed probability of `0.01` (1%) and `5` degrees of freedom.  
   **Result**: 15.086

3. `=CHIINV(A1, B1)`  
   Computes the chi-squared statistic for the probability in cell `A1` and the degrees of freedom in cell `B1`.

### Notes:

- The `probability` value represents the area under the chi-squared curve to the right of the corresponding chi-squared
  value.
- The function requires both arguments to be positive; otherwise, it will return an error.
- If `degrees_freedom` is **non-integer**, it is truncated to the nearest integer.
- As of Excel 2010, `CHIINV` has been replaced by `CHISQ.INV.RT` for improved accuracy and functionality. `CHIINV` is
  still available for compatibility with older versions of Excel.

### Use Cases:

- **Critical Value Determination**: Identify the chi-squared critical value for a given significance level in hypothesis
  testing.
- **Goodness-of-Fit Test**: Help decide whether an observed data distribution matches the expected.
- **Contingency Table Analysis**: Determine significance in independence testing.

> **Tip**: In newer versions of Excel, use `CHISQ.INV.RT` for better precision and compatibility.