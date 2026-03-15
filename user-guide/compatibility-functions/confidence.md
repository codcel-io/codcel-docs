<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CONFIDENCE Function

The `CONFIDENCE` function in Excel is used to calculate the confidence interval for a population mean based on a given
significance level, standard deviation, and sample size. It helps you understand the range within which the true
population mean is likely to fall.

### Key Features of CONFIDENCE:

- Calculates the **margin of error** for a population mean.
- Useful in **statistical analysis** to estimate population parameters.
- Based on the assumption that the data follows a **normal distribution**.

### Syntax:

```plaintext
CONFIDENCE(alpha, standard_dev, size)
```

- **alpha**: The significance level used to compute the confidence level. For example, if the confidence level is 95%,
  then `alpha = 1 - 0.95 = 0.05`.
- **standard_dev**: The standard deviation of the population.
- **size**: The size of the sample.

### Examples:

1. `=CONFIDENCE(0.05, 1.5, 100)`  
   Calculates the margin of error for a 95% confidence level (`alpha = 0.05`), a standard deviation of `1.5`, and a
   sample size of `100`.  
   **Result**: The margin of error, which can be added to or subtracted from the sample mean to determine the confidence
   interval.

2. `=CONFIDENCE(0.01, 2.0, 50)`  
   Returns the margin of error for a 99% confidence level (`alpha = 0.01`), with a standard deviation of `2.0` and a
   sample size of `50`.  
   **Result**: The margin of error.

### Notes:

- The **confidence level** is defined as `1 - alpha`. For example:
    - If `alpha = 0.05`, the confidence level is **95%**.
    - If `alpha = 0.01`, the confidence level is **99%**.
- The `size` argument must be greater than 1, and the `standard_dev` must be a positive number, or the function will
  return a `#NUM!` error.
- If `alpha` is less than or equal to 0 or greater than or equal to 1, Excel will return a `#NUM!` error.
- A higher confidence level (lower `alpha`) results in a wider confidence interval.

### Formula Behind CONFIDENCE:

The `CONFIDENCE` function calculates the margin of error using the formula:

```plaintext
CONFIDENCE = Z × (σ / √n)
```

Where:

- `Z`: The Z-score corresponding to the confidence level.
- `σ`: The population standard deviation (`standard_dev`).
- `n`: The sample size (`size`).

### Use Cases:

- **Market Research**: Calculate the confidence interval for survey results to estimate population preferences.
- **Quality Assurance**: Determine the confidence interval for a manufacturing process's mean output.
- **Statistical Reporting**: Provide a range for population parameters based on sample data.

> **Tip**: Use the `CONFIDENCE.NORM` function in newer versions of Excel, as it provides the same functionality but is
more standardized for clarity.