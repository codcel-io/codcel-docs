<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOGNORM.INV Function

The `LOGNORM.INV` function in Excel is used to calculate the inverse of the lognormal cumulative distribution function (
CDF) for a given probability, mean, and standard deviation of a dataset. It is particularly useful in financial analysis
and probability scenarios where data follows a lognormal distribution.

### Key Features of LOGNORM.INV:

- Returns the value `x` such that the probability of a lognormal random variable being less than or equal to `x` equals
  the given probability.
- Useful in modeling and simulations where data is skewed, such as stock prices or financial returns.
- Based on the parameters of the normal distribution of the corresponding logarithmic values.

### Syntax:

```plaintext
LOGNORM.INV(probability, mean, standard_dev)
```

- **probability**: A probability associated with the lognormal distribution (required).
- **mean**: The mean of the natural logarithms of the dataset (required).
- **standard_dev**: The standard deviation of the natural logarithms of the dataset (required).

### How It Works:

The `LOGNORM.INV` function computes the value `x` using the lognormal distribution such that:

```plaintext
P(X ≤ x) = probability
```

Where:

- `X` is the lognormal random variable.
- The log of `X` follows a normal distribution with the specified `mean` and `standard_dev`.

### Examples:

1. **Basic Calculation**:

   Find the inverse lognormal value for `probability = 0.95`, `mean = 0`, and `standard_dev = 1`:
   ```excel
   =LOGNORM.INV(0.95, 0, 1)
   ```
   Result: Approximately `5.180251602`.

2. **Using Real-World Parameters**:

   Suppose you are modeling financial returns with a probability of `0.8`, and the mean and standard deviation of the
   log-transformed returns are `1.2` and `0.5`, respectively:
   ```excel
   =LOGNORM.INV(0.8, 1.2, 0.5)
   ```
   Result: The value `x` that satisfies the condition will be returned.

3. **Testing a Range of Probabilities**:

   If you have multiple probabilities listed in range `A1:A5`, and you want to compute the inverse lognormal values for
   a `mean` of `1.5` and a `standard_dev` of `0.7`:
   ```excel
   =LOGNORM.INV(A1, 1.5, 0.7)
   ```

### Notes:

- **Parameter Constraints**:
    - The `probability` must be between `0` and `1` (exclusive).
    - The `standard_dev` must be greater than `0`.
- If any parameters are invalid or out of bounds, Excel returns a `#NUM!` error.
- This function is the inverse of the `LOGNORM.DIST` function for cumulative distribution mode.

### Applications:

- **Financial Analysis**: Estimating potential stock prices or returns based on their lognormal distribution.
- **Risk Assessment**: Modeling uncertain scenarios in project management or investment returns.
- **Simulation Models**: Generating input values for stochastic (probabilistic) models where the variable follows a
  lognormal distribution.

> **Tip:** Use the `LOGNORM.INV` function to back-calculate values for specific probabilities in datasets that are
lognormally distributed.