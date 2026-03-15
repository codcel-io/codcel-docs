<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## T.DIST.RT Function

The `T.DIST.RT` function in Excel is used to **return the one-tailed probability of the Student's t-distribution**,
which is
commonly applied in hypothesis testing, particularly for evaluating the significance of a t-value in the right tail of
the distribution.

This function calculates the cumulative probability in the right tail of the t-distribution from a specified t-value
based on the degrees of freedom.

### Key Features of T.DIST.RT:

- **One-Tailed Right Probability**: Computes the cumulative probability associated with the right side (tail) of the
  distribution.
- **Degrees of Freedom**: Uses the specified degrees of freedom to define the shape of the t-distribution.
- Applicable in one-tailed hypothesis testing when evaluating if a sample mean is significantly greater than the
  population mean.

### Syntax:

```plaintext
T.DIST.RT(x, degrees_freedom)
```

- **x**: Required. The numeric value at which to evaluate the right-tailed probability (t-value).
- **degrees_freedom**: Required. The number of degrees of freedom that characterize the t-distribution shape.

### How It Works:

The function calculates the area under the right tail of the t-distribution beyond the specified t-value (`x`). This
represents the probability of observing a t-value greater than the given `x`.

### Examples:

1. **Right-Tail Probability:**
   Calculate the cumulative probability for a t-value of `2.5` with `10` degrees of freedom:

   ```excel
   =T.DIST.RT(2.5, 10)
   ```

   This will return the right-tailed probability for the given t-value of `2.5`.

2. **One-Tailed Hypothesis Testing:**
   Suppose your t-statistic is `1.96` with `20` degrees of freedom, and you want to determine the probability of getting
   a t-value greater than `1.96`:

   ```excel
   =T.DIST.RT(1.96, 20)
   ```

   This provides the p-value for the right-tailed test.

### Notes:

- **Input Validations**:
    - Both arguments (`x` and `degrees_freedom`) must be numeric values.
    - The `degrees_freedom` must be greater than 0.
- **Output Details**:
    - The function returns the cumulative probability for the right tail of the t-distribution.
    - This value can be interpreted as the p-value in certain one-tailed hypothesis tests.
- **Errors**:
    - `#NUM!` if `degrees_freedom <= 0`.
    - `#VALUE!` if the inputs are non-numeric.

### Applications:

- **One-Tailed Hypothesis Testing**: Evaluate the p-value when testing if a sample mean is significantly larger than the
  population mean.
- **Critical Region Testing**: Analyze the likelihood of observing a t-value more extreme than the critical value in the
  positive/right direction.
- **Statistical Models**: Assess probabilities in scenarios involving small sample sizes where t-distribution is
  preferred over the normal distribution.

> **Tip**: Use the `T.DIST` function for left-tail probabilities and `T.DIST.2T` for two-tailed probabilities when your
analysis involves deviations in both directions.