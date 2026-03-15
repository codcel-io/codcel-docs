<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FINV Function

The `FINV` function in Excel is used to calculate the **inverse of the F-distribution**. It determines the critical
value (i.e., the value of `x`) for a given probability and degrees of freedom, making it particularly useful in
hypothesis testing scenarios, such as **ANOVA (Analysis of Variance)** or comparing variances between two datasets.

### Key Features of FINV:

- Returns the critical value associated with a given probability in the F-distribution.
- Useful for finding the value of `x` that results in the cumulative F-distribution equaling the specified probability.
- Often used in **tests of equality of variances** between two populations.

### Syntax:

```plaintext
FINV(probability, degrees_freedom1, degrees_freedom2)
```

- **probability**: The significance level or cumulative probability for which you want to find the corresponding `x`.
  Must be between 0 and 1.
- **degrees_freedom1**: The numerator degrees of freedom. Must be a positive integer.
- **degrees_freedom2**: The denominator degrees of freedom. Must also be a positive integer.

### Example:

1. **Critical Value**  
   `=FINV(0.05, 4, 6)`  
   Calculates the critical value `x` for a cumulative probability of 0.05 (5% significance level) with 4 numerator
   degrees of freedom and 6 denominator degrees of freedom.  
   **Result**: The critical value of the F-statistic for this F-distribution.

### Notes:

- The **F-distribution** is a right-skewed distribution used in statistical tests that compare variances.
- **Invalid inputs**:
    - **probability** < 0 or > 1 will result in a `#NUM!` error.
    - Non-positive integers for **degrees_freedom1** or **degrees_freedom2** will result in a `#NUM!` error.
- Use the `FDIST` function to find the probability for a given `x` instead of the inverse.

### Use Cases:

- **Hypothesis Testing**: Use FINV to find the critical F-value for determining whether variances or group means differ
  significantly.
- **ANOVA Testing**: Helps compute critical F-values in evaluating whether mean differences across groups are
  significant.
- **Regression Analysis**: Identify critical thresholds for F-statistics when comparing the goodness-of-fit among
  regression models.

> **Tip**: For cases where you need the inverse at the **right tail**, use the related function `F.INV.RT` for better
precision with modern Excel versions.