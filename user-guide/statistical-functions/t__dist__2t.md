<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## T.DIST.2T Function

The `T.DIST.2T` function in Excel is used to **return the two-tailed Student's t-distribution probability**, which is
widely utilized in hypothesis testing to evaluate the significance of a t-value for both tails of the distribution.

This function calculates the cumulative probability for both sides (tails) of the t-distribution, based on a given
t-value and degrees of freedom.

### Key Features of T.DIST.2T:

- **Two-Tailed Probability**: Computes the cumulative probability for both tails of the distribution.
- **Degrees of Freedom**: Adjusts the shape of the t-distribution using the specified degrees of freedom.
- Used in hypothesis testing scenarios when you're concerned about deviations in *both* directions (i.e., it's not
  restricted to left or right-tailed tests).

### Syntax:

```plaintext
T.DIST.2T(x, degrees_freedom)
```

- **x**: Required. The numeric value at which to evaluate the two-tailed probability (t-value).
- **degrees_freedom**: Required. The number of degrees of freedom defining the t-distribution shape.

### How It Works:

The function computes the cumulative probability above and below the specified t-value (i.e., in both tails of the
distribution). For example, given a t-value of `t`, it will calculate the sum of the probabilities in the lower tail (
less than `-t`) and the upper tail (greater than `t`).

### Examples:

1. **Two-Tailed Probability**:
   Find the two-tailed cumulative probability for a t-value of `2.5` with `10` degrees of freedom:

   ```excel
   =T.DIST.2T(2.5, 10)
   ```

   This will return the probability for both tails of the t-distribution.

2. **Critical Region Testing**:
   Suppose you calculate a t-statistic of `1.96` with `20` degrees of freedom and want to know the probability of
   obtaining a t-value more extreme than ±1.96:

   ```excel
   =T.DIST.2T(1.96, 20)
   ```

   This gives the combined probability in the lower tail (less than `-1.96`) and the upper tail (greater than `1.96`).

### Notes:

- **Input Validations**:
    - Both arguments (`x` and `degrees_freedom`) must be numeric.
    - The `degrees_freedom` must be greater than 0.
- **Output Details**:
    - The result is the total two-tailed cumulative probability for the given inputs.
    - This value is often used as the p-value in two-tailed hypothesis testing.
- **Errors**:
    - `#NUM!` if `degrees_freedom <= 0`.
    - `#VALUE!` if the inputs are non-numeric.

### Applications:

- **Two-Tailed Hypothesis Testing**: Determine the p-value in a test to evaluate if a sample mean significantly differs
  from the population mean in *either* direction.
- **Statistical Modeling**: Analyze confidence intervals or extreme observation probabilities in small sample data.
- **Probability Estimation**: Evaluate two-tailed probabilities for deviations in both directions.

> **Tip**: Use the `T.DIST` function for left-tailed probabilities and `T.DIST.RT` for right-tailed probabilities when
testing one-tailed hypotheses.