<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHISQ.DIST Function

The `CHISQ.DIST` function in Excel calculates the **Chi-Square distribution**, which is widely used in hypothesis
testing and statistical analysis to compare observed data with expected data under a specific hypothesis. The Chi-Square
distribution is particularly useful for categorical data and in scenarios such as independence testing or
goodness-of-fit.

This function can compute either the **probability density function** (PDF) or the **cumulative distribution function
** (CDF) for the Chi-Square distribution, based on the value of its arguments.

### Key Features of CHISQ.DIST:

- Computes probabilities or cumulative probabilities for the Chi-Square distribution.
- Useful in statistical tests, such as the Chi-Square test for independence or goodness of fit.

### Syntax:

```plaintext
CHISQ.DIST(x, degrees_freedom, cumulative)
```

- **x**: The value at which you want to evaluate the distribution. Must be a non-negative number.
- **degrees_freedom**: The number of degrees of freedom in the distribution. Must be a positive integer.
- **cumulative**: A logical value (`TRUE` or `FALSE`) that specifies the form of the distribution:
    - If `TRUE`, `CHISQ.DIST` returns the cumulative distribution function (CDF), the probability that the observed
      value is less than or equal to `x`.
    - If `FALSE`, it returns the probability density function (PDF).

### Examples:

1. `=CHISQ.DIST(5, 3, TRUE)`  
   Calculates the cumulative probability for a Chi-Square distribution with 3 degrees of freedom at `x = 5`.  
   **Result**: `0.91608`.

2. `=CHISQ.DIST(2, 2, FALSE)`  
   Returns the probability density function (PDF) for a Chi-Square distribution with 2 degrees of freedom at `x = 2`.  
   **Result**: `0.18394`.

3. `=CHISQ.DIST(10, 4, TRUE)`  
   Computes the cumulative probability for a Chi-Square distribution where `degrees_freedom = 4` and `x = 10`.  
   **Result**: `0.98651`.

### Notes:

- The **Chi-Square distribution** is used to test statistical hypotheses, especially for categorical data with multiple
  categories.
- If `x < 0` or if `degrees_freedom` is not a positive integer, the function returns an error (`#NUM!` or `#VALUE!`).
- For small degrees of freedom, the Chi-Square distribution is skewed to the left. With larger degrees of freedom, the
  distribution becomes symmetrical.

> **Tip**: Use the `CHISQ.DIST` function when testing the relationship between observed and expected data under a
> theoretical model, such as in contingency tables or for analyzing variances.