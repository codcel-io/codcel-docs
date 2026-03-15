<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## T.INV Function

The `T.INV` function in Excel is used to **return the t-value associated with a given probability and degrees of freedom
**, based on the Student's t-distribution.

This function is useful in statistical analyses, particularly in hypothesis testing and confidence interval
calculations, to determine the critical t-value corresponding to a specified probability.

### Key Features of T.INV:

- **Inverse T-Distribution**: Computes the t-value for a specific probability in the left tail of the t-distribution.
- **Degrees of Freedom**: Uses the specified degrees of freedom to define the shape of the t-distribution.
- Applicable for deriving critical t-values in one-tailed hypothesis tests or confidence intervals.

### Syntax:

```plaintext
T.INV(probability, degrees_freedom)
```

- **probability**: Required. A numeric value representing the cumulative probability for the left tail of the
  distribution (must be between 0 and 1).
- **degrees_freedom**: Required. A positive numeric value representing the degrees of freedom that govern the shape of
  the t-distribution.

### How It Works:

The `T.INV` function calculates the t-value such that the area under the t-distribution curve to the left of this
t-value equals the specified cumulative probability. Thus, it essentially reverses the `T.DIST` function.

### Examples:

1. **Left-Tail Critical Value:**
   Determine the t-value for a cumulative probability of `0.025` with `10` degrees of freedom:

   ```excel
   =T.INV(0.025, 10)
   ```

   This will return the t-value such that the left tail beyond this point has a probability of `0.025`.

2. **Confidence Interval Calculation:**
   For a 95% confidence interval and `15` degrees of freedom, calculate the critical t-value for the two-tailed test (
   use 0.975 for the left-tail cumulative probability):

   ```excel
   =T.INV(0.975, 15)
   ```

   This provides the t-value for a 95% confidence interval.

### Notes:

- **Input Validations**:
    - `probability` must lie between 0 and 1. Otherwise, the function will return the `#NUM!` error.
    - `degrees_freedom` must be greater than 0; otherwise, the function will throw the `#NUM!` error.
    - If non-numeric inputs are provided, the function will return the `#VALUE!` error.

- **Output Details**:
    - Returns the critical t-value corresponding to the specified cumulative probability.
    - Can output both negative and positive t-values, depending on the cumulative probability.

- **Errors**:
    - `#NUM!` is returned if `probability` is less than 0 or greater than 1, or if `degrees_freedom <= 0`.
    - `#VALUE!` is returned if either argument is non-numeric.

### Applications:

- **Hypothesis Testing**: Identify critical t-values for one-tailed or two-tailed statistical tests.
- **Confidence Interval Estimation**: Calculate the margin of error for confidence intervals involving small sample
  sizes.
- **Critical Region Analysis**: Define boundaries in the t-distribution to assess the significance of test statistics.

> **Tip**: For two-tailed tests, remember to split the alpha level (e.g., use `alpha/2` for `probability`) so the
corresponding t-value reflects the desired confidence level across both tails.