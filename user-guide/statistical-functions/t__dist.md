<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## T.DIST Function

The `T.DIST` function in Excel is used to **return the probability density (p-value) of the left-tailed Student's
t-distribution**, which is widely utilized in hypothesis testing and statistical significance analysis.

This function calculates probabilities based on a t-value, degrees of freedom, and specifies whether the distribution is
cumulative (area under the curve) or the probability density function (PDF) value.

### Key Features of T.DIST:

- **Left-Tailed Probability**: Computes the cumulative probability from negative infinity to the given t-value for the
  Student's t-distribution.
- **Degrees of Freedom**: Requires the degrees of freedom to adjust the shape of the t-distribution.
- **Cumulative Option**: Allows you to calculate either the cumulative probability or the probability density function
  value.

### Syntax:

```plaintext
T.DIST(x, degrees_freedom, cumulative)
```

- **x**: Required. The numeric value at which to evaluate the distribution (t-value).
- **degrees_freedom**: Required. The number of degrees of freedom for the t-distribution.
- **cumulative**: Required. A logical value:
    - `TRUE` if you want the cumulative distribution function (CDF).
    - `FALSE` if you want the probability density function (PDF).

### How It Works:

- A **cumulative distribution function (CDF)** computes the probability that the t-distribution is less than or equal to
  the given t-value.
- The **probability density function (PDF)** calculates the height of the probability distribution curve at the given
  t-value.

### Examples:

1. **Cumulative Probability**:
   Find the cumulative probability for a t-value of `2.5` with `10` degrees of freedom:

   ```excel
   =T.DIST(2.5, 10, TRUE)
   ```

   This will return the cumulative probability from negative infinity to `2.5`.

2. **Probability Density**:
   Get the probability density value for the same t-value (`2.5`) and degrees of freedom (`10`):

   ```excel
   =T.DIST(2.5, 10, FALSE)
   ```

   This calculates the density of the t-distribution at `x = 2.5`.

3. **Practical Use for Left Tail**:
   Suppose you calculate a t-statistic of `-1.96` with `20` degrees of freedom, and you are interested in the
   left-tailed cumulative probability:

   ```excel
   =T.DIST(-1.96, 20, TRUE)
   ```

   This result can be used in hypothesis testing to determine the p-value.

### Notes:

- **Input Validations**:
    - The `degrees_freedom` must be greater than or equal to `1`.
    - The `cumulative` parameter can only accept `TRUE` or `FALSE`.
- **Output Details**:
    - A `TRUE` cumulative result gives the area under the curve to the left of `x`.
    - A `FALSE` result returns the height of the curve (density) at the specific value of `x`.
- **Errors**:
    - `#NUM!` if `degrees_freedom < 1`.
    - `#VALUE!` if inputs are non-numeric.

### Applications:

- **Statistical Testing**: Compute p-values for left-tailed t-tests to test hypotheses.
- **Probability Analysis**: Evaluate areas under the t-distribution to determine probabilities.
- **Data Science**: Use the t-distribution in modeling and analyzing small-sample data or when population variance is
  unknown.

> **Tip**: Use the `T.DIST.RT` function to calculate right-tail probabilities, or `T.DIST.2T` for two-tailed
probabilities when required.