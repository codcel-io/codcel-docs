<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## F.DIST.RT Function

The `F.DIST.RT` function in Excel calculates the **right-tailed F-distribution**, which is used to determine the
probability that the observed F-statistic value (or a more extreme value) would occur under the null hypothesis. This
function is commonly used in hypothesis testing, particularly in **ANOVA (Analysis of Variance)** and F-tests, to assess
if two data sets have significantly different variances.

### Key Features of F.DIST.RT:

- Computes the one-tailed or **right-tailed probability** of the F-distribution.
- Useful for **hypothesis testing** involving variance comparisons or model fits.
- Provides the probability that the observed value or larger values occur when the null hypothesis is true.

### Syntax:

```plaintext
F.DIST.RT(x, degrees_freedom1, degrees_freedom2)
```

- **x**: The value at which the function evaluates the F-distribution. This is the calculated F-statistic (positive
  number).
- **degrees_freedom1**: The numerator degrees of freedom of the data set.
- **degrees_freedom2**: The denominator degrees of freedom of the data set.

### Examples:

1. **Hypothesis testing with a calculated F-statistic:**

   ```excel
   =F.DIST.RT(2.5, 5, 10)
   ```

   This calculates the right-tailed probability for an F-statistic of 2.5, with numerator degrees of freedom = 5 and
   denominator degrees of freedom = 10. The result shows the probability that an F-statistic greater than or equal to
   2.5 occurs under the null hypothesis.

2. **Using results in a decision rule for hypothesis testing:**

   Suppose your calculated F-statistic is in cell `A1`:

   ```excel
   =F.DIST.RT(A1, 4, 15)
   ```

   This calculates the right-tailed probability for the F-statistic stored in `A1`, with numerator degrees of freedom =
   4 and denominator degrees of freedom = 15. Compare the result to your significance level (e.g., 0.05) to determine
   whether to reject the null hypothesis.

### Notes:

- The `x` value must be positive. If `x` ≤ 0, `F.DIST.RT` returns a `#NUM!` error.
- Both `degrees_freedom1` and `degrees_freedom2` must be greater than 0. If either is invalid, the function will return
  a `#NUM!` error.
- `F.DIST.RT` focuses on the **right-tail**, while `F.DIST` allows for both cumulative and point-density probabilities.

### Applications:

- **ANOVA (Analysis of Variance):** Assess whether variances between groups are significantly different.
- **Regression Analysis:** Evaluate significance of predictors by comparing models.
- **Hypothesis Testing:** Determine probabilities for observed variance ratios to test assumptions of equality.

> **Tip:** Use `F.DIST.RT` alongside related statistical functions like `F.TEST` and `F.INV` for comprehensive
hypothesis testing and critical value determination in Excel.