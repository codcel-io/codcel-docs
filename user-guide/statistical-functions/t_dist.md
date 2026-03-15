<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TDIST Function

The `TDIST` function in Excel is used to **return the probability (p-value) of the Student's t-distribution**, which is
commonly used to test hypotheses and evaluate statistical significance in data analysis. This function calculates either
the one-tailed or two-tailed probability based on the t-value and degrees of freedom provided.

### Key Features of TDIST:

- **Statistical Probability**: Computes the probability associated with the Student's t-distribution.
- **Hypothesis Testing**: Useful for determining the likelihood of observing a t-value as extreme or more extreme than
  what is expected under the null hypothesis.
- **Flexibility**: Allows calculation for both one-tailed and two-tailed distributions.

### Syntax:

```plaintext
TDIST(x, degrees_freedom, tails)
```

- **x**: Required. The absolute value of the t-statistic.
- **degrees_freedom**: Required. The number of degrees of freedom for the t-distribution.
- **tails**: Required. Specifies the number of tails for the distribution:
    - `1` if you want the one-tailed probability.
    - `2` if you want the two-tailed probability.

### How It Works:

The t-distribution formula involves complex calculations, but Excel handles it for you based on the input parameters.
Here’s a summary of its usage:

- A **one-tailed test** computes the probability that a value is greater than or less than a specific t-value.
- A **two-tailed test** computes the probability that a value falls in either tail of the distribution, important for
  tests where deviations in both directions are considered.

### Examples:

1. **One-Tailed Test**:
   Suppose you want the probability of obtaining a t-value of `2.5` with `10` degrees of freedom in a **one-tailed test
   **:

   ```excel
   =TDIST(2.5, 10, 1)
   ```

   This will return the probability of observing a t-value greater than `2.5`.

2. **Two-Tailed Test**:
   For the same t-value (`2.5`) and degrees of freedom (`10`) but for a **two-tailed test**:

   ```excel
   =TDIST(2.5, 10, 2)
   ```

   This value will be twice the one-tailed probability, as it includes the tails on both sides of the distribution.

3. **Practical Hypothesis Testing**:
   If your t-statistic is calculated as `1.96` with `20` degrees of freedom, and you want to find the two-tailed
   p-value:

   ```excel
   =TDIST(1.96, 20, 2)
   ```

   This result helps you decide whether to reject the null hypothesis at a specific significance level.

### Notes:

- **Input Validations**:
    - The `x` parameter must be a positive number. Use the absolute value of your t-statistic.
    - `degrees_freedom` must be greater than or equal to `1` (whole numbers only).
    - `tails` must be either `1` or `2`.
- **Errors**:
    - `#NUM!` if `x < 0`, `degrees_freedom < 1`, or `tails` is not `1` or `2`.
    - `#VALUE!` if inputs are non-numeric.

### Applications:

- **Statistical Inference**: Evaluate p-values for t-tests in various scenarios (e.g., comparing means of two groups).
- **Hypothesis Testing**: Determine whether to reject or fail to reject the null hypothesis.
- **Scientific Analysis**: Use the t-distribution to test data for significance in fields such as biology, economics,
  and engineering.
- **Quality Control**: Analyze deviations in production or measurement systems.

> **Tip**: The `TDIST` function is commonly used in conjunction with t-tests (e.g., `TTEST`) for in-depth statistical
analysis. If you're using newer Excel versions, consider using `T.DIST` for more advanced capabilities and support for
left-tailed probabilities.