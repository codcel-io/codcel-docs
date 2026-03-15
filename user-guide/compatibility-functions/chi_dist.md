<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHIDIST Function

The `CHIDIST` function in Excel returns the one-tailed probability of the chi-squared distribution. It is generally used
in hypothesis testing to evaluate how likely it is that an observed distribution is due to chance, based on the
chi-squared statistic and degrees of freedom.

### Key Features of CHIDIST:

- Computes the **right-tailed probability** of the chi-squared distribution.
- Often used in **goodness-of-fit tests** or tests for independence in contingency tables.
- Assists in determining whether a difference between expected and observed data is statistically significant.

### Syntax:

```plaintext
CHIDIST(x, degrees_freedom)
```

- **x**: The value at which to evaluate the distribution (must be ≥ 0).
- **degrees_freedom**: The number of degrees of freedom (must be ≥ 1).

### Examples:

1. `=CHIDIST(10.5, 5)`  
   Calculates the right-tailed probability for a chi-squared value of `10.5` with `5` degrees of freedom.  
   **Result**: The probability value (e.g., 0.0615).

2. `=CHIDIST(3.2, 2)`  
   Returns the right-tailed probability for a chi-squared statistic of `3.2` and `2` degrees of freedom.  
   **Result**: The probability value.

3. `=CHIDIST(A1, B1)`  
   Computes the probability for the chi-squared statistic in cell `A1` and degrees of freedom in `B1`.

### Notes:

- The function works only for positive values of `x` and degrees of freedom; otherwise, it returns an error.
- If degrees of freedom is **non-integer**, it is truncated to the nearest integer.
- As of Excel 2010, `CHIDIST` has been replaced by the more precise and robust `CHISQ.DIST.RT` function, but it is still
  available for compatibility with older versions.

### Use Cases:

- **Goodness-of-Fit Test**: Determine if a sample matches an expected distribution.
- **Independence Testing**: Check if two variables in a contingency table are independent.

> **Tip**: Use `CHISQ.DIST.RT` for improved accuracy in newer versions of Excel.