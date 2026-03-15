<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SKEW Function

The `SKEW` function in Excel is used to **return the skewness of a distribution**. Skewness is a statistical measure
that
indicates the asymmetry of a dataset's distribution around its mean. It helps you understand whether the data is more
concentrated on one side of the mean or evenly distributed.

### Key Features of SKEW:

- **Positive Skew**: If the result is greater than `0`, the distribution has a longer tail on the right side (towards
  higher values).
- **Negative Skew**: If the result is less than `0`, the distribution has a longer tail on the left side (towards lower
  values).
- **Symmetry**: A result of `0` indicates a perfectly symmetrical distribution.

### Syntax:

```plaintext
SKEW(number1, [number2], ...)
```

- **number1, number2, ...**: Required. One or more numbers or ranges to calculate the skewness. At least three data
  points are required for the calculation.

### How It Works:

The `SKEW` function evaluates the shape of a distribution by comparing the mean, median, and individual data points. It
calculates skewness using the following formula:

```math
SKEW = (n / [(n-1)(n-2)]) * Σ((xi - x̄)³ / s³)
```

Where:

- `n`: Number of data points.
- `xi`: Each individual data point.
- `x̄`: The mean (average) of the dataset.
- `s`: The standard deviation of the dataset.

- **Positive skew**: Indicates more data is concentrated below the mean, with outliers pulling the tail to the right.
- **Negative skew**: Indicates more data is concentrated above the mean, with outliers pulling the tail to the left.

### Examples:

1. **Positive Skew**:
   If the numbers `{2, 4, 6, 8, 100}` are provided:
   ```excel
   =SKEW(2, 4, 6, 8, 100)
   ```
   Result: `1.5926` (A strongly positively skewed distribution as 100 is an outlier on the right).

2. **Negative Skew**:
   For the numbers `{50, 51, 52, 53, 10}`:
   ```excel
   =SKEW(50, 51, 52, 53, 10)
   ```
   Result: `-1.3093` (This indicates a negatively skewed distribution with 10 as a left-side outlier).

3. **Near Symmetry**:
   For a more symmetrical dataset like `{10, 20, 30, 40, 50}`:
   ```excel
   =SKEW(10, 20, 30, 40, 50)
   ```
   Result: `0` (The distribution is symmetrical, with no skew).

### Notes:

- **Minimum Requirements**:
    - The dataset must include at least three data points. Otherwise, the function returns a `#DIV/0!` error.
- **Non-Numeric Data**:
    - Text, logical values, or empty cells within the data range are ignored in the calculation.
- **Outliers' Impact**:
    - Skewness is highly sensitive to outliers. A few extreme values can strongly influence the result.
- **Symmetry Indicator**:
    - Although a result of `0` implies symmetry, it does not guarantee a normal distribution.

### Applications:

- **Descriptive Statistics**: Analyze data's asymmetry in research and reports.
- **Financial Analysis**: Assess risk in returns distributions (e.g., stock performance often shows skewness).
- **Quality Control**: Identify biases in processes or measurements.
- **Data Science**: Evaluate data distribution to choose appropriate statistical models or transformations.

> **Tip**: Complement the `SKEW` function with the `KURT` function to explore both skewness and kurtosis (the "
> tailedness" of the distribution).