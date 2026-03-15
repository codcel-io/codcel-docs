<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORMDIST Function

The `NORMDIST` function in Excel is used to **calculate the normal distribution** for a given value.  
The normal distribution is a bell-shaped curve used to represent data that is evenly distributed around a mean.

### Key Features of NORMDIST:

- Computes the probability density or cumulative probability of a value based on the normal distribution.
- Useful for statistical analysis, such as evaluating probabilities, z-scores, or distributions in data.

### Syntax:

```plaintext
NORMDIST(x, mean, standard_dev, cumulative)
```

- **x**: Required. The value for which you want to calculate the distribution.
- **mean**: Required. The mean (average) of the distribution.
- **standard_dev**: Required. The standard deviation of the distribution.
- **cumulative**: Required. A logical value that determines the type of distribution to be calculated:
    - `TRUE`: Returns the cumulative distribution function (CDF), the probability that `x` is less than or equal to a
      value.
    - `FALSE`: Returns the probability density function (PDF), the height of the distribution curve at `x`.

### How It Works:

The `NORMDIST` function uses the formulas for either the cumulative or probability density function of the normal
distribution:

1. **Probability Density Function (PDF)**:
   For `cumulative = FALSE`, the formula used is:
   ```plaintext
   PDF = (1 / (standard_dev * SQRT(2 * PI))) * EXP(-(x - mean)^2 / (2 * standard_dev^2))
   ```
   This computes the height of the normal distribution at `x`.

2. **Cumulative Distribution Function (CDF)**:
   For `cumulative = TRUE`, the function uses integration to calculate the area under the curve to the left of `x`.

### Examples:

1. **Basic Example (PDF)**:
   To calculate the probability density for `x = 50`, with a mean of `45` and standard deviation of `10`:
   ```excel
   =NORMDIST(50, 45, 10, FALSE)
   ```
   Result: `0.0352065`.

2. **Cumulative Distribution Example (CDF)**:
   To find the cumulative probability that a value is less than or equal to `70`, where the distribution has a mean of
   `65` and a standard deviation of `15`:
   ```excel
   =NORMDIST(70, 65, 15, TRUE)
   ```
   Result: `0.630558`.

3. **Real-Life Scenario**:
   A company tracks its employees' test scores, which follow a normal distribution with a mean of `80` and a standard
   deviation of `10`. To determine the probability of a score below `90`:
   ```excel
   =NORMDIST(90, 80, 10, TRUE)
   ```
   Result: `0.841345`.

### Notes:

- **Input Validation**:
    - If **standard_dev** is `0` or negative, the function returns `#NUM!`.
    - If any input is non-numeric, the function returns `#VALUE!`.

- **Choosing Between PDF and CDF**:
    - Use `FALSE` for probability density when you are interested in the height of the curve at a specific point.
    - Use `TRUE` for cumulative probability when you need the total probability up to a point.

- **Output Ranges**:
    - The cumulative probability (`cumulative = TRUE`) output value is always between `0` and `1`.
    - The probability density (`cumulative = FALSE`) is not bounded between `0` and `1`.

### Applications:

- **Statistical Analysis**: Evaluate normal probabilities for statistical tasks like hypothesis testing or data
  modeling.
- **Finance**: Calculate probabilities for returns, prices, or risk analysis.
- **Quality Control**: Check how a measurement compares to a process's mean.
- **Healthcare**: Model probabilities of data based on patient statistics.

> **Tip**: The `NORMDIST` function was replaced by the `NORM.DIST` function in Excel 2010 and later versions, which
supports similar functionality with enhanced features.