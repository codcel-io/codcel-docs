<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORM.DIST Function

The `NORM.DIST` function in Excel is used to **calculate the normal distribution for a given value**.  
This can be the probability density function (PDF) or cumulative distribution function (CDF) depending on the input.  
It is a versatile function commonly used in statistics, data analysis, and probability modeling.

### Key Features of NORM.DIST:

- Returns the normal distribution value for a specified mean and standard deviation.
- Can calculate the **cumulative distribution function (CDF)** or **probability density function (PDF)**.
- Useful in analyzing data distributions and probabilities for bell-curves.

### Syntax:

```plaintext
NORM.DIST(x, mean, standard_dev, cumulative)
```

- **x**: Required. The value for which you want the distribution.
- **mean**: Required. The arithmetic mean (average) of the distribution.
- **standard_dev**: Required. The standard deviation of the distribution.
- **cumulative**: Required. A logical value that determines the type of distribution to calculate:
    - `TRUE`: Calculates the **cumulative distribution function (CDF)**, i.e., the probability that a random variable is
      less than or equal to `x`.
    - `FALSE`: Calculates the **probability density function (PDF)**, i.e., the likelihood of `x` occurring at a given
      mean and standard deviation.

### How It Works:

1. When `cumulative = TRUE`, the function computes the area under the normal distribution curve to the left of `x`.
2. When `cumulative = FALSE`, the function computes the height of the curve (PDF) at the given point `x`.

The general formula used is based on the normal distribution equation:

```plaintext
f(x) = (1 / (√2π * σ)) * e^(-(x - μ)² / (2σ²))
```

Where:

- `μ` is the mean.
- `σ` is the standard deviation.
- `x` is the input value.
- `e` is Euler's number (~2.71828).

### Examples:

1. **Cumulative Normal Distribution**:
   Suppose the average test score is `70` with a standard deviation of `10`, and you want the cumulative probability for
   a score of `80`:
   ```excel
   =NORM.DIST(80, 70, 10, TRUE)
   ```
   Result: `0.8413` (Approximately 84.13%).

2. **Probability Density Function**:
   For the same test score example above, calculate the likelihood of exactly scoring `80` using the PDF:
   ```excel
   =NORM.DIST(80, 70, 10, FALSE)
   ```
   Result: `0.0242` (Approximately 2.42%).

3. **Applications in Business**:
   In a market analysis, assume a product sells an average of 100 units a week with a standard deviation of 15 units.
   You can calculate the cumulative probability of selling 120 or fewer units:
   ```excel
   =NORM.DIST(120, 100, 15, TRUE)
   ```

4. **Understanding Outliers**:
   Use the PDF function to determine the probability of a rare event falling far from the mean. For example, the
   likelihood of a test score of `50` when the mean is `70` and the standard deviation is `10`:
   ```excel
   =NORM.DIST(50, 70, 10, FALSE)
   ```

### Notes:

- **Input Validation**:
    - If `standard_dev <= 0`, the function returns `#NUM!`.
    - If any parameter is non-numeric, the function returns `#VALUE!`.

- **Precision**:
    - The computed results are based on numerical integration techniques for the cumulative distribution.

### Applications:

- **Statistical Analysis**: Analyze probabilities and likelihoods for data that is normally distributed (bell-curve).
- **Financial Risk Assessment**: Estimate probabilities for stock price margins, sales, or returns.
- **Quality Control**: Detect outliers in manufacturing or production processes.
- **Machine Learning**: Preprocessing and understanding distributions in datasets.

> **Tip:** Use `NORM.INV` to calculate the inverse of this function, i.e., to find the value `x` given a probability and
normal distribution parameters.