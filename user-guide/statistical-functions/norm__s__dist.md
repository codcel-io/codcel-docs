<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORM.S.DIST Function

The `NORM.S.DIST` function in Excel is used to **calculate the standard normal distribution**, which is a normal
distribution with a mean of 0 and a standard deviation of 1. This function returns either the cumulative probability or
the probability density value for a given `z`-score.

### Key Features of NORM.S.DIST:

- Works with the **Z-distribution** (standard normal distribution).
- Can calculate:
    - **Cumulative probability**: The probability that a random variable is less than or equal to a specified value.
    - **Density function**: The value of the probability density function for the input `z`.

### Syntax:

```plaintext
NORM.S.DIST(z, cumulative)
```

- **z**: Required. The z-value for which you want to calculate the distribution.
- **cumulative**: Required (TRUE or FALSE). This determines the type of result:
    - `TRUE`: Returns the cumulative distribution function (CDF).
    - `FALSE`: Returns the probability density function (PDF).

### How It Works:

1. The **cumulative distribution function** gives the probability that a value is less than or equal to the specified
   `z`. It represents the area under the curve to the left of `z`.
2. The **probability density function** provides the height of the curve at a given `z`, which is useful for examining
   the relative likelihood of `z`.

The formula for the standard normal distribution's PDF is:

```plaintext
f(z) = (1 / √(2π)) * e^(-z² / 2)
```

Where `z` is the standard score.

The CDF cannot be expressed in closed form, but Excel uses numerical methods to compute it.

### Examples:

1. **Cumulative Distribution Example**:
   Find the cumulative probability for a z-value of 1.5:
   ```excel
   =NORM.S.DIST(1.5, TRUE)
   ```
   Result: `0.933193`.

   This means there’s a 93.32% chance a random variable from the standard normal distribution will fall below 1.5.

2. **Probability Density Example**:
   Find the height of the standard normal curve at `z = 0`:
   ```excel
   =NORM.S.DIST(0, FALSE)
   ```
   Result: `0.398942`.

   This represents the peak value of the curve (since the mean of the standard normal distribution is 0).

3. **Tail Area Example**:
   Calculate the probability of a z-value greater than 2.33. Subtract the cumulative probability from 1:
   ```excel
   =1 - NORM.S.DIST(2.33, TRUE)
   ```
   Result: `0.009902`.

   This indicates a very small chance (0.99%) of obtaining a value greater than 2.33.

### Notes:

- **Interpretation of z**:
    - A negative `z` represents a value below the mean.
    - A positive `z` represents a value above the mean.
- **Input Validation**:
    - If `z` is non-numeric, the function returns `#VALUE!`.
    - If `cumulative` is not a valid boolean (TRUE or FALSE), the function returns an error.

### Applications:

- **Statistics and Testing**: Commonly used in hypothesis testing and confidence interval calculations.
- **Financial Modeling**: Used for risk analysis and stock price modeling under normality assumptions.
- **Quality Control**: Helps in standardizing variables and identifying outliers in a dataset.

> **Tip:** For normal distributions with other means and standard deviations, use the `NORM.DIST` function, which allows
specifying these parameters.