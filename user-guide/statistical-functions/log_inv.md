<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOGINV Function

The `LOGINV` function in Excel is used to calculate the **inverse of the log-normal cumulative distribution** for a
given probability. It is typically applied in scenarios involving data that follows a log-normal distribution, such as
modeling stock prices, reliability analysis, or financial risk calculations.

### Key Features of LOGINV:

- **Inverse Cumulative Distribution**: Returns the value `x` for which the cumulative log-normal distribution equals the
  given probability.
- **Modeling Skewed Data**: Useful for datasets where values are naturally skewed and cannot be modeled effectively by
  normal distributions.
- **Probabilistic Analysis**: Helps in determining critical thresholds based on probabilities.

### Syntax:

```plaintext
LOGINV(probability, mean, standard_dev)
```

- **probability**: The cumulative probability associated with the log-normal distribution. This must be a value between
  0 and 1.
- **mean**: The mean (μ) of the natural logarithm of the distribution. This is the location parameter of the log-normal
  distribution.
- **standard_dev**: The standard deviation (σ) of the natural logarithm of the distribution. This is the scale parameter
  of the log-normal distribution.

### How It Works:

The `LOGINV` function calculates the value `x` using the inverse of the log-normal distribution function. The log-normal
distribution is characterized by its mean (μ) and standard deviation (σ) after a natural logarithmic transformation.

The log-normal cumulative distribution function (CDF) is given by:

```plaintext
P(X ≤ x) = Φ((ln(x) - μ) / σ)
```

Where:

- `Φ` represents the cumulative distribution function of the standard normal distribution.

The `LOGINV` function essentially reverses this process to find `x` when a specific cumulative probability `P` is given.

### Examples:

1. **Basic Calculation**:

   Find the value `x` for a cumulative probability `0.9` with a mean of `0` and standard deviation of `1`:

   ```excel
   =LOGINV(0.9, 0, 1)
   ```
   Result: The value of `x` such that 90% of the data falls below it.

2. **Practical Scenario**:

   Suppose the prices of a product are log-normally distributed with a mean of `2.5` (logarithmic) and standard
   deviation of `0.5` (logarithmic). Calculate the price that corresponds to the top 5% cutoff:

   ```excel
   =LOGINV(0.95, 2.5, 0.5)
   ```
   Result: The price at the 95th percentile of the distribution.

3. **Using LOGINV to Set Probabilistic Targets**:

   A financial analyst uses a log-normal model to predict stock prices. Given a historical mean return of `0.03` and
   volatility (std dev) of `0.2`, the analyst calculates the maximum price with a `99%` probability:

   ```excel
   =LOGINV(0.99, 0.03, 0.2)
   ```

### Notes:

- **Range of Probability**: The `probability` value must be between 0 and 1. Values outside this range result in a
  `#NUM!` error.
- **Logarithmic Transformation**: The `mean` and `standard_dev` are not the raw data values—they are transformed using
  the natural logarithm. Ensure your inputs are consistent with this requirement.
- **Non-Negative Output**: The result of `LOGINV` is always a positive number since the log-normal distribution does not
  allow negative values.

### Applications:

- **Stock Price Modeling**: Predict stock prices based on a log-normal assumption.
- **Risk Management**: Identify critical thresholds for risk probabilities in financial portfolios.
- **Engineering Reliability**: Assess product lifetimes and failure rates.
- **Demand Modeling**: Use probabilistic thresholds to set inventory reorder points in logistics.

> **Tip:** If you want to calculate the log-normal cumulative distribution (instead of its inverse), use the
`LOGNORM.DIST` function.