<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOGNORM.DIST Function

The `LOGNORM.DIST` function in Excel is used to **return values from a log-normal distribution**, which is a probability
distribution of a random variable whose logarithm is normally distributed. It is particularly helpful for working with
data that is positively skewed, such as financial models, biological data, or engineering applications.

### Key Features of LOGNORM.DIST:

- **Probability Distribution Analysis**: Calculates probabilities or distribution values based on the log-normal
  distribution.
- **Supports Cumulative or Non-cumulative Values**: You can decide between the probability density function (PDF) or
  cumulative density function (CDF).
- Useful for modeling data where values cannot drop below zero and grow exponentially.

### Syntax:

```plaintext
LOGNORM.DIST(x, mean, standard_dev, cumulative)
```

- **x**: The value for which you want the log-normal distribution. It must be a positive number.
- **mean**: The mean (average) of the natural logarithm of the distribution.
- **standard_dev**: The standard deviation of the natural logarithm of the distribution. This must be a positive number.
- **cumulative**: A logical value (`TRUE` or `FALSE`) specifying the type of distribution:
    - `TRUE` for the cumulative log-normal distribution (CDF).
    - `FALSE` for the probability density function (PDF).

### How It Works:

The `LOGNORM.DIST` function assumes that for a log-normal distribution:

- If `ln(x)` follows a normal distribution with a specified mean and standard deviation, `x` follows a log-normal
  distribution.
- Depending on whether `cumulative` is `TRUE` or `FALSE`, the function either computes the cumulative probability up to
  `x` or the probability density at `x` itself.

### Examples:

1. **Basic Calculation (Cumulative Distribution)**:
   Calculate the cumulative log-normal distribution for `x = 4`, where the logarithmic mean is `0.5` and standard
   deviation is `1`:
   ```excel
   =LOGNORM.DIST(4, 0.5, 1, TRUE)
   ```
   Result: `0.588852`

2. **Basic Calculation (Probability Density Function)**:
   Calculate the probability density for `x = 4` with the same mean and standard deviation:
   ```excel
   =LOGNORM.DIST(4, 0.5, 1, FALSE)
   ```
   Result: `0.126317`

3. **Using with Financial Data**:
   Suppose you have stock prices and want to calculate the probability that they fall within a specific range. If the
   prices follow a log-normal distribution, you can use `LOGNORM.DIST` to assess probabilities.

### Notes:

- **Parameter Constraints**:
    - `x` must always be a positive value; otherwise, the function returns a `#NUM!` error.
    - Both `mean` and `standard_dev` should be real numbers, with `standard_dev` greater than zero.
    - If any argument is invalid (e.g., `mean` is non-numeric), the function will return a `#VALUE!` error.

- **Special Cases**:
    - When `cumulative` is `TRUE`, the result represents the probability that a randomly selected value is less than or
      equal to `x`.
    - The PDF version (`cumulative = FALSE`) helps identify the likelihood of observing a specific value.

### Applications:

- **Financial Modeling**: Analyze stock returns or other positively skewed financial data using a log-normal
  distribution model.
- **Risk Analysis**: Model outcomes for positively skewed processes.
- **Environmental Studies**: Study data distributions, such as pollutant levels, that often follow a log-normal pattern.
- **Quality Control**: Assess production data or component reliability following log-normal characteristics.

> **Tip:** Combine `LOGNORM.DIST` with other statistical functions to perform complex analyses, such as evaluating
probability regions or fitting models to datasets. For visual representation, plot values or cumulative probabilities in
Excel charts.