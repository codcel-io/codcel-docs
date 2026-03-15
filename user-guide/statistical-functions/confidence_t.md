<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CONFIDENCE.T Function

The `CONFIDENCE.T` function in Excel calculates the **confidence interval** for a population mean when using a *
*t-distribution**. This function is particularly useful when the sample size is small and the population standard
deviation is unknown.

It is commonly used in statistical analysis to estimate the margin of error for a population mean, especially for
datasets with smaller sample sizes.

### Key Features of CONFIDENCE.T:

- Computes the confidence value using the t-distribution.
- Suitable for creating confidence intervals when the sample standard deviation is used instead of the population
  standard deviation.
- Ideal for scenarios with smaller sample sizes or when the population standard deviation is unknown.

### Syntax:

```plaintext
CONFIDENCE.T(alpha, standard_dev, size)
```

- **alpha**: The desired significance level for the confidence interval. For a confidence level of 95%, use
  `alpha = 1 - 0.95` (i.e., 0.05).
- **standard_dev**: The sample standard deviation. Must be a positive number.
- **size**: The sample size. Must be a positive integer.

### Examples:

1. `=CONFIDENCE.T(0.05, 1.5, 10)`  
   Computes the confidence value for a 95% confidence level, with a sample standard deviation of 1.5 and a sample size
   of 10.  
   **Result**: `1.0472639`.

2. `=CONFIDENCE.T(0.01, 2, 15)`  
   Determines the confidence value for a 99% confidence level, with a sample standard deviation of 2 and a sample size
   of 15.  
   **Result**: `1.847056`.

3. `=CONFIDENCE.T(0.1, 3, 8)`  
   Calculates the confidence value for a 90% confidence level, with a sample standard deviation of 3 and a sample size
   of 8.  
   **Result**: `2.776531347`.

### Notes:

- The confidence interval around the mean can be calculated as: `Mean ± CONFIDENCE.T(alpha, standard_dev, size)`.
- If `alpha` is ≤ 0 or ≥ 1, or if `standard_dev` or `size` is non-positive, the function returns an error (`#NUM!` or
  `#VALUE!`).
- This function assumes that the data follows a t-distribution, which is suitable for small sample sizes or when the
  population standard deviation is not available.

> **Tip**: Use `CONFIDENCE.T` for reliable estimation of population means when working with small samples or unknown
population parameters.