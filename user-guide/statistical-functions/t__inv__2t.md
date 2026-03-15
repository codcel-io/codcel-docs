<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## T.INV.2T Function

The `T.INV.2T` function in Excel is used to **return the t-value for the two-tailed Student's t-distribution**, given a
probability and degrees of freedom. This function is commonly used when performing hypothesis tests to find critical
values of the t-distribution.

### Key Features of T.INV.2T:

- **Critical Value Computation**: Calculates the t-value corresponding to a cumulative probability in a two-tailed
  t-distribution.
- **Hypothesis Testing**: Useful for determining critical values when testing statistical hypotheses in fields such as
  biology, engineering, and social sciences.
- **Two-Tailed Only**: Specifically designed for two-tailed distributions.

### Syntax:

```plaintext
T.INV.2T(probability, degrees_freedom)
```

- **probability**: Required. The probability associated with the two-tailed t-distribution. This value must be between 0
  and 1 (exclusive).
- **degrees_freedom**: Required. The number of degrees of freedom for the t-distribution. This must be a positive
  integer.

### How It Works:

The `T.INV.2T` function calculates the t-value such that the area under the t-distribution curve for a two-tailed test
equals the provided probability. It essentially finds the value of `t` that corresponds to a combined area in both tails
of the distribution.

### Examples:

1. **Find Critical t-Value**:
   Suppose you have a two-tailed test with a significance level of `0.05` (so the combined probability in both tails is
   `0.05`) and `15` degrees of freedom. You can find the critical t-value like this:

   ```excel
   =T.INV.2T(0.05, 15)
   ```

   This will return the t-value that corresponds to a 5% probability in the two tails of the t-distribution.

2. **Determine Critical Values for 95% Confidence Interval**:
   To calculate the critical t-value for a 95% confidence level (leaving 5% in both tails combined), use:

   ```excel
   =T.INV.2T(0.05, 20)
   ```

   The result is the t-value beyond which the extremes lie for both ends of the distribution.

3. **Building a Hypothesis Test**:
   For a two-tailed test, if your alpha value is `0.01` (1% significance level) and you have `10` degrees of freedom:

   ```excel
   =T.INV.2T(0.01, 10)
   ```

   This critical value helps you decide whether your test statistic falls in the rejection region.

### Notes:

- **Input Validations**:
    - `probability` must be between `0` and `1` (non-inclusive). If it is `<= 0` or `>= 1`, the function will return a
      `#NUM!` error.
    - `degrees_freedom` must be greater than `0`. If it is less than or equal to `0`, the function will also return a
      `#NUM!` error.
    - If the inputs are non-numeric, the function will return a `#VALUE!` error.

- **Relationship to Other Functions**:
    - The `T.INV.2T` function is related to `T.DIST.2T`, which computes the cumulative probability for a given t-value
      in the two-tailed t-distribution.
    - If you only need a **one-tailed t-test**, you would use `T.INV` instead of `T.INV.2T`.

### Applications:

- **Statistical Inference**: Use the critical values to evaluate whether a test statistic falls within a confidence
  interval.
- **Confidence Intervals**: Find cutoff points for two-tailed confidence intervals in means and regressions.
- **Hypothesis Testing**: Validate null or alternative hypotheses with two-tailed t-tests.

> **Tip**: The `T.INV.2T` function is most directly used in significance testing. Consider using this function to
> complement hypothesis testing workflows involving `T.DIST` or `T.TEST`.