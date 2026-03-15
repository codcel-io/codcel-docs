<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## F.TEST Function

The `F.TEST` function in Excel calculates the **two-tailed probability** that the variances between two data sets are
significantly different. It is primarily used in statistical applications, including **comparison of variances** in
hypothesis testing.

### Key Features of F.TEST:

- Computes the **probability** that two data sets have the same variance.
- Useful in hypothesis testing to evaluate whether two samples come from populations with identical variances.
- Often used in conjunction with the `F.DIST` or `F.INV` functions for statistical analysis.

### Syntax:

```plaintext
F.TEST(array1, array2)
```

- **array1**: The first array or range of data.
- **array2**: The second array or range of data.

### Examples:

1. **Calculate the two-tailed probability for two data sets:**

   Suppose you have the two sets of data:

    - `Array1`: {4, 5, 6, 7, 8}
    - `Array2`: {9, 10, 11, 12, 13}

   To compare their variances, use the formula:

    ```excel
    =F.TEST(A1:A5, B1:B5)
    ```

   This calculates the p-value representing the probability that the variances of `Array1` and `Array2` are equal.

2. **Hypothesis testing for equal variances:**

   If you are conducting a test with null hypothesis `H0: σ1² = σ2²` (variances are equal) and alternative hypothesis
   `Ha: σ1² ≠ σ2²` (variances are different):

    ```excel
    =F.TEST(Data1Range, Data2Range)
    ```

   The p-value from the `F.TEST` function tells you if the variances are significantly different. If the p-value is *
   *less than the significance level (e.g., α = 0.05)**, you reject the null hypothesis.

### Notes:

- The `F.TEST` function returns a **two-tailed p-value**.
- If the data arrays have insufficient length or contain invalid data, the function may return `#VALUE!` or `#N/A`
  errors.
- It assumes the data are normally distributed in order to calculate probabilities accurately.

### Applications:

- **Hypothesis Testing:** Evaluate if variances between two groups or treatments differ significantly.
- **Regression Analysis:** Compare the variance of residuals in two models.
- **Analysis of Variance (ANOVA):** Preliminarily check for equal variances between groups before conducting ANOVA.

> **Tip:** Use `F.TEST` with supporting statistical functions, like `F.INV` or `F.DIST.RT`, for more advanced variance
analysis and decision-making in hypothesis testing.