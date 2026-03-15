<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## F.INV.RT Function

The `F.INV.RT` function in Excel calculates the **inverse of the (right-tailed) F-distribution**. It is used to
determine the critical value of the F-statistic for a given probability and degrees of freedom in statistical
applications like **hypothesis testing** and **Analysis of Variance (ANOVA)**.

### Key Features of F.INV.RT:

- Computes the **critical value** of the F-distribution for **right-tailed probabilities**.
- Useful in hypothesis testing to determine **critical thresholds** for F-tests in right-tailed scenarios.
- Often used in conjunction with `F.DIST.RT` and `F.DIST` for statistical analysis.

### Syntax:

```plaintext
F.INV.RT(probability, degrees_freedom1, degrees_freedom2)
```

- **probability**: The right-tailed probability associated with the F-distribution. This must be a value between 0 and
  1.
- **degrees_freedom1**: The numerator degrees of freedom of the data set.
- **degrees_freedom2**: The denominator degrees of freedom of the data set.

### Examples:

1. **Calculate the critical value for a given right-tailed probability and degrees of freedom:**

    ```excel
    =F.INV.RT(0.05, 4, 6)
    ```

   This calculates the F-statistic value corresponding to a 5% right-tailed probability, with 4 numerator degrees of
   freedom and 6 denominator degrees of freedom.

2. **Use in determining rejection regions for hypothesis testing:**

   Suppose you are conducting a one-tailed test with a significance level of `α = 0.05`, and you know the degrees of
   freedom:

    ```excel
    =F.INV.RT(0.05, 10, 20)
    ```

   This calculates the critical F-statistic for a 95% confidence level in a right-tailed test using 10 and 20 degrees of
   freedom.

### Notes:

- If **probability** is less than 0 or greater than 1, `F.INV.RT` returns the `#NUM!` error.
- Both **degrees_freedom1** and **degrees_freedom2** must be greater than 0. Otherwise, the function returns the `#NUM!`
  error.
- The `F.INV.RT` function calculates the **right-tailed critical value** directly, making it suitable for tests
  requiring thresholds for smaller probabilities.

### Applications:

- **ANOVA (Analysis of Variance):** Determine critical values for comparing group variances.
- **Regression Analysis:** Evaluate F-statistics for model significance in right-tailed tests.
- **Hypothesis Testing:** Calculate critical values to define decision rules for rejecting the null hypothesis in
  right-tailed tests.

> **Tip:** Use `F.INV.RT` alongside other statistical functions like `F.INV` and `F.DIST.RT` to perform thorough
statistical analysis and hypothesis testing in Excel.