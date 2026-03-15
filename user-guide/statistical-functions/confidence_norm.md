<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CONFIDENCE.NORM Function

The `CONFIDENCE.NORM` function in Excel calculates the **confidence interval** for a population mean, based on a normal
distribution. This function is frequently used in statistics to determine the margin of error for a population mean with
a specified confidence level.

It computes the confidence value required to create a confidence interval for a population mean, given a known standard
deviation and sample size.

### Key Features of CONFIDENCE.NORM:

- Calculates the confidence value for a normal distribution.
- Useful for creating confidence intervals in statistical analysis.
- Applications include quality control, scientific experiments, and population surveys.

### Syntax:

```plaintext
CONFIDENCE.NORM(alpha, standard_dev, size)
```

- **alpha**: The desired significance level for the confidence interval. For a confidence level of 95%, use
  `alpha = 1 - 0.95` (i.e., 0.05).
- **standard_dev**: The population standard deviation. Must be a positive number.
- **size**: The sample size. Must be a positive integer.

### Examples:

1. `=CONFIDENCE.NORM(0.05, 1.5, 50)`  
   Computes the confidence value for a 95% confidence level, with a standard deviation of 1.5 and a sample size of 50.  
   **Result**: `0.414179265`.

2. `=CONFIDENCE.NORM(0.01, 2, 100)`  
   Determines the confidence value for a 99% confidence level, with a standard deviation of 2 and a sample size of
   100.  
   **Result**: `0.516336616`.

3. `=CONFIDENCE.NORM(0.1, 3, 25)`  
   Calculates the confidence value for a 90% confidence level, with a standard deviation of 3 and a sample size of 25.  
   **Result**: `1.011357605`.

### Notes:

- The confidence interval around the mean can be calculated as: `Mean ± CONFIDENCE.NORM(alpha, standard_dev, size)`.
- If `alpha` is ≤ 0 or ≥ 1, or if `standard_dev` or `size` is non-positive, the function returns an error (`#NUM!` or
  `#VALUE!`).
- Ensure that the population follows a normal distribution when using this function for accuracy.

> **Tip**: Use `CONFIDENCE.NORM` for precise estimation of population means, particularly in scenarios where the
population standard deviation is known and the sample size is large.