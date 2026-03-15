<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TINV Function

The `TINV` function in Excel is used to **return the critical t-value (inverse of the Student's t-distribution)**
based on a given probability and the degrees of freedom. This function is often used in statistical hypothesis testing
to determine threshold values for rejecting the null hypothesis in t-tests.

### Key Features of TINV:

- **Critical t-Value Calculation**: Computes the t-value such that the probability of observing a more extreme value is
  equal to the specified input.
- **Hypothesis Testing**: Useful for setting bounds for significance levels in t-tests.
- **Two-Tailed Probabilities**: This function specifically works with two-tailed probabilities.

### Syntax:

```plaintext
TINV(probability, degrees_freedom)
```

- **probability**: Required. The probability associated with the two-tailed t-distribution.
    - Must be between `0` and `1`.
- **degrees_freedom**: Required. The number of degrees of freedom for the t-distribution.

### How It Works:

The `TINV` function essentially inverts the cumulative distribution function (CDF) of the t-distribution to obtain the
critical t-value. For a given probability and degrees of freedom:

- A **two-tailed test** divides the probability equally into both tails.
- The function returns the positive critical value, which is the absolute value of the t-statistic threshold.

For example, if the function returns `2.5`, the critical region for the two-tailed test spans from `-2.5` to `2.5`.

### Examples:

1. **Calculating a Critical t-Value**:
   Suppose you want the critical t-value for a significance level of `0.05` (5%) with `10` degrees of freedom for a
   two-tailed test:

   ```excel
   =TINV(0.05, 10)
   ```

   This will return the critical t-value corresponding to a 95% confidence interval.

2. **Changing the Degrees of Freedom**:
   For the same significance level (`0.05`), but with `20` degrees of freedom:

   ```excel
   =TINV(0.05, 20)
   ```

   As you increase the degrees of freedom, the critical t-value gets smaller, reflecting a closer approximation to the
   normal distribution.

3. **Critical Value for 99% Confidence Interval**:
   If you need the critical t-value for a 99% confidence interval (significance level of `0.01`) with `15` degrees of
   freedom:

   ```excel
   =TINV(0.01, 15)
   ```

   The smaller significance level results in a larger critical t-value, capturing more extreme values in the tails.

### Notes:

- **Input Validations**:
    - `probability` must be greater than `0` and less than `1`.
    - `degrees_freedom` must be an integer greater than or equal to `1`.
- **Error Handling**:
    - `#NUM!` if `probability` is not within the valid range (`0 < probability < 1`).
    - `#VALUE!` if non-numeric values are used as inputs.

### Applications:

- **Statistical Hypothesis Testing**: Determine thresholds for rejecting the null hypothesis in two-tailed t-tests.
- **Confidence Intervals**: Find critical values for constructing confidence intervals for population means.
- **Scientific Analysis**: Useful in data analysis in fields such as economics, psychology, and biomedical research.
- **Experimental Design**: Set significance thresholds for experiments comparing small sample sizes.

> **Tip**: In newer versions of Excel, consider using the `T.INV.2T` function for improved accuracy and support for
> one-tailed distributions (`T.INV`).