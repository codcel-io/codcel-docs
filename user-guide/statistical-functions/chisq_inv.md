<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHISQ.INV Function

The `CHISQ.INV` function in Excel calculates the **inverse of the left-tailed probability** of the Chi-Square
distribution. It is often used in statistical hypothesis testing to determine critical values for Chi-Square tests, such
as goodness-of-fit tests or tests of independence.

This function essentially finds the value of the Chi-Square statistic corresponding to a specified cumulative
probability (left-tailed probability) and a given number of degrees of freedom.

### Key Features of CHISQ.INV:

- Computes the Chi-Square statistic (critical value) for a given left-tailed probability.
- Helps determine threshold values for statistical hypothesis testing.
- Used widely in statistical analyses involving Chi-Square distribution.

### Syntax:

```plaintext
CHISQ.INV(probability, degrees_freedom)
```

- **probability**: The cumulative probability (left-tailed) for which you want to find the Chi-Square critical value.
  Must be between 0 and 1.
- **degrees_freedom**: The number of degrees of freedom. Must be a positive integer.

### Examples:

1. `=CHISQ.INV(0.95, 3)`  
   Finds the Chi-Square critical value that corresponds to a left-tailed probability of `0.95` with `3` degrees of
   freedom.  
   **Result**: `0.215795283`.

2. `=CHISQ.INV(0.5, 5)`  
   Finds the Chi-Square value corresponding to a left-tailed probability of `0.5` with `5` degrees of freedom.  
   **Result**: `4.351460191`.

3. `=CHISQ.INV(0.85, 2)`  
   Calculates the Chi-Square critical value for `0.85` cumulative probability with `2` degrees of freedom.  
   **Result**: `4.999L82602`.

### Notes:

- The function is particularly useful when determining critical values for Chi-Square tests, which help decide whether
  to reject the null hypothesis.
- If `probability` is ≤ 0 or > 1, or if `degrees_freedom` is not a positive integer, the function returns an error (
  `#NUM!` or `#VALUE!`).
- For large degrees of freedom, the Chi-Square distribution begins to resemble a normal distribution.

> **Tip**: Use `CHISQ.INV` to compute the critical thresholds against which you compare observed Chi-Square statistics
> in your hypothesis tests. This can help determine the statistical significance of your results.