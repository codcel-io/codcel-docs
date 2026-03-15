<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHISQ.DIST.RT Function

The `CHISQ.DIST.RT` function in Excel computes the **right-tailed probability** of the Chi-Square distribution. This
function is commonly used in hypothesis testing, particularly to evaluate the statistical significance in Chi-Square
tests, such as goodness-of-fit tests or tests of independence.

The right-tailed probability represents the area under the Chi-Square curve to the right of a specified value (i.e., the
probability of observing a value greater than or equal to the given value under the Chi-Square distribution).

### Key Features of CHISQ.DIST.RT:

- Computes the right-tailed probability for a given Chi-Square value.
- Widely used in statistical hypothesis tests involving categorical data.
- Helps to determine whether a result is statistically significant.

### Syntax:

```plaintext
CHISQ.DIST.RT(x, degrees_freedom)
```

- **x**: The value at which you want the right-tailed probability. Must be a non-negative number.
- **degrees_freedom**: The number of degrees of freedom. Must be a positive integer.

### Examples:

1. `=CHISQ.DIST.RT(5, 3)`  
   Computes the right-tailed probability for a Chi-Square value of `5` with `3` degrees of freedom.  
   **Result**: `0.172115629`.

2. `=CHISQ.DIST.RT(10, 4)`  
   Calculates the probability in the right tail of the Chi-Square curve for `10` with `4` degrees of freedom.  
   **Result**: `0.040427681`.

3. `=CHISQ.DIST.RT(2, 1)`  
   Finds the probability in the right tail of the Chi-Square distribution for `x = 2` and `1` degree of freedom.  
   **Result**: `0.157299207`.

### Notes:

- The **right-tailed Chi-Square probability** is useful when testing for the significance of observed results in
  statistical analyses.
- If `x < 0` or `degrees_freedom` is not a positive integer, the function returns an error (`#NUM!` or `#VALUE!`).
- With fewer degrees of freedom, the Chi-Square distribution is skewed to the right. With many degrees of freedom, it
  approximates a normal distribution.

> **Tip**: Use `CHISQ.DIST.RT` to directly compute p-values for Chi-Square tests, which help determine if the null
hypothesis can be rejected based on observed data.