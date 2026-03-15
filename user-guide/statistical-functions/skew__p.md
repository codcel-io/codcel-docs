<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SKEW.P Function

The `SKEW.P` function in Excel is used to **return the population skewness of a distribution**. Skewness is a
statistical measure that indicates the asymmetry of a dataset's distribution around its mean for the **entire population
**. It helps you understand whether the data is more concentrated on one side of the mean or evenly distributed.

### Key Features of SKEW.P:

- **Positive Skew**: If the result is greater than `0`, the distribution has a longer tail on the right side (towards
  higher values).
- **Negative Skew**: If the result is less than `0`, the distribution has a longer tail on the left side (towards lower
  values).
- **Symmetry**: A result of `0` indicates a perfectly symmetrical distribution.

### Syntax:

```plaintext
SKEW.P(number1, [number2], ...)
```

- **number1, number2, ...**: Required. One or more numbers or ranges to calculate the population skewness. At least
  three data points are required for the calculation.

### How It Works:

The `SKEW.P` function evaluates the shape of the **population data distribution** by comparing the mean, median, and
individual data points. It calculates skewness using the following formula:

```math
SKEW.P = (1 / n) * Σ((xi - x̄)³ / s³)
```

Where:

- `n`: Number of data points (population size).
- `xi`: Each individual data point.
- `x̄`: The mean (average) of the dataset.
- `s`: The standard deviation of the dataset.

- **Positive skew**: Indicates more data is concentrated below the mean, with outliers pulling the tail to the right.
- **Negative skew**: Indicates more data is concentrated above the mean, with outliers pulling the tail to the left.

### Examples:

1. **Positive Skew**:
   For the numbers `{2, 4, 6, 8, 100}`:
   ```excel
   =SKEW.P(2, 4, 6, 8, 100)
   ```
   Result: `1.5926` (A strongly positively skewed distribution as 100 is an outlier on the right).

2. **Negative Skew**:
   For the numbers `{50, 51, 52, 53, 10}`:
   ```excel
   =SKEW.P(50, 51, 52, 53, 10)
   ```
   Result: `-1.3093` (A negatively skewed distribution with 10 as a left-side outlier).

3. **Symmetrical Distribution**:
   For a more symmetrical dataset like `{10, 20, 30, 40, 50}`:
   ```excel
   =SKEW.P(10, 20, 30, 40, 50)
   ```
   Result: `0` (The distribution is symmetrical, with no skew).

### Notes:

- **Minimum Requirements**:
    - At least three data points are required. Otherwise, the function returns a `#DIV/0!` error.
- **Non-Numeric Data**:
    - Text, logical values, or empty cells within the data range are ignored in the calculation.
- **Impact of Outliers**:
    - Skewness is highly sensitive to outliers. A few extreme values can strongly influence the result.
- **Difference Between `SKEW` and `SKEW.P`**:
    - While `SKEW` calculates skewness for a sample dataset, `SKEW.P` calculates it for the entire population.

### Applications:

- **Descriptive Statistics**: Analyze the asymmetry of population-level data distribution.
- **Financial Analysis**: Assess population skewness in large datasets, like entire market returns.
- **Quality Assurance**: Examine asymmetrical biases in population-scale processes or measurements.
- **Data Science**: Explore population data distribution when selecting statistical models or transformations.

> **Tip**: Use `SKEW.P` when working with complete population data and `SKEW` for sample-based datasets.