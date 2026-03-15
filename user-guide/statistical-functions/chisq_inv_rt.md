<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHISQ.INV.RT Function

The `CHISQ.INV.RT` function in Excel calculates the **inverse of the right-tailed probability** of the Chi-Square
distribution. This function is widely used in statistical hypothesis testing to find critical values for Chi-Square
tests when working with right-tailed probabilities.

It essentially determines the Chi-Square statistic value that corresponds to a specified cumulative right-tailed
probability and a given number of degrees of freedom.

### Key Features of CHISQ.INV.RT:

- Computes the Chi-Square statistic (critical value) for a given right-tailed probability.
- Useful for statistical hypothesis testing, such as tests of independence or goodness-of-fit tests.
- Helps in determining threshold values for rejecting null hypotheses in Chi-Square tests.

### Syntax:

```plaintext
CHISQ.INV.RT(probability, degrees_freedom)
```

- **probability**: The cumulative probability (right-tailed) for which you want to find the Chi-Square critical value.
  Must be between 0 and 1.
- **degrees_freedom**: The number of degrees of freedom. Must be a positive integer.

### Examples:

1. `=CHISQ.INV.RT(0.05, 3)`  
   Finds the Chi-Square critical value corresponding to a right-tailed probability of `0.05` with `3` degrees of
   freedom.  
   **Result**: `7.814727903`.

2. `=CHISQ.INV.RT(0.2, 5)`  
   Finds the Chi-Square critical value for a right-tailed probability of `0.2` with `5` degrees of freedom.  
   **Result**: `6.064425843`.

3. `=CHISQ.INV.RT(0.01, 2)`  
   Calculates the Chi-Square critical value that corresponds to a right-tailed probability of `0.01` with `2` degrees of
   freedom.  
   **Result**: `9.210340372`.

### Notes:

- The function is essential for determining threshold values in statistical hypothesis testing where the right-tailed
  probability is used.
- If `probability` is ≤ 0 or > 1, or if `degrees_freedom` is not a positive integer, the function returns an error (
  `#NUM!` or `#VALUE!`).
- For large degrees of freedom, the Chi-Square distribution tends to resemble a normal distribution.
- Right-tailed probabilities are particularly important for tests where the rejection region lies in the upper tail of
  the Chi-Square distribution.

> **Tip**: Leverage `CHISQ.INV.RT` for hypothesis testing scenarios where the critical region is in the upper tail of
the Chi-Square distribution. It is especially useful for determining critical values to compare against observed
Chi-Square statistics.