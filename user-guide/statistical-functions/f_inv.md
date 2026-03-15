<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## F.INV Function

The `F.INV` function in Excel calculates the **inverse of the F-distribution**. This is used to determine the critical
value of the F-statistic for a given probability and degrees of freedom in statistical applications such as hypothesis
testing and **Analysis of Variance (ANOVA)**.

### Key Features of F.INV:

- Computes the **F distribution critical value** for a given cumulative probability.
- Useful in hypothesis testing to determine **critical thresholds** for F-tests.
- Often used in conjunction with `F.DIST.RT` and `F.DIST` to evaluate statistical hypotheses.

### Syntax:

```plaintext
F.INV(probability, degrees_freedom1, degrees_freedom2)
```

- **probability**: The cumulative probability associated with the F-distribution. This must be a value between 0 and 1.
- **degrees_freedom1**: The numerator degrees of freedom of the data set.
- **degrees_freedom2**: The denominator degrees of freedom of the data set.

### Examples:

1. **Calculate the critical value for a given probability and degrees of freedom:**

    ```excel
    =F.INV(0.95, 4, 6)
    ```

   This calculates the F-statistic value corresponding to a cumulative probability of 0.95, with 4 numerator degrees of
   freedom and 6 denominator degrees of freedom. This critical value is often used to determine whether to reject the
   null hypothesis.

2. **Use in determining rejection regions for hypothesis testing:**

   Suppose you know the level of significance (e.g., `α = 0.05`) and degrees of freedom:

    ```excel
    =F.INV(1 - 0.05, 10, 20)
    ```

   This calculates the critical F-statistic for a 95% confidence level using 10 and 20 degrees of freedom.

### Notes:

- If **probability** is less than 0 or greater than 1, `F.INV` returns the `#NUM!` error.
- Both **degrees_freedom1** and **degrees_freedom2** must be greater than 0. If invalid, the function returns the
  `#NUM!` error.
- The `F.INV` function calculates the **left-tailed critical value**. For right-tailed critical values, consider using
  `1 - probability` as an input.

### Applications:

- **ANOVA (Analysis of Variance):** Determine thresholds for comparing variances between groups.
- **Regression Analysis:** Evaluate critical values for testing model significance.
- **Hypothesis Testing:** Calculate critical values to define decision rules for rejecting the null hypothesis.

> **Tip:** Use `F.INV` alongside related statistical functions like `F.INV.RT` and `F.DIST.RT` for comprehensive
statistical analysis and hypothesis testing in Excel.