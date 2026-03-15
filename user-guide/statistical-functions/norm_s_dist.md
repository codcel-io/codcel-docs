<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORMSDIST Function

The `NORMSDIST` function in Excel is used to **calculate the standard normal cumulative distribution** function (CDF)
for a given `z`-score. This function determines the probability that a random variable in a standard normal distribution
is less than or equal to the given `z`.

### Key Features of NORMSDIST:

- *Standard Normal Distribution*: The function assumes a standard normal distribution with a mean of `0` and a standard
  deviation of `1`.
- Converts `z`-scores into probabilities for the standard normal distribution.
- Useful in statistical analysis to compare data points or calculate probabilities.

### Syntax:

```plaintext
NORMSDIST(z)
```

- **z**: Required. The `z`-score for which you want to calculate the cumulative distribution.

### How It Works:

The `NORMSDIST` function evaluates the cumulative probability of a random variable in a standard normal distribution
being less than or equal to the given `z`. Mathematically, it calculates the value of the cumulative distribution
function (CDF) for the standard normal distribution:

```plaintext
NORMSDIST(z) = (1 / SQRT(2 * PI)) * Integrate[EXP(-t^2 / 2)] from -∞ to z
```

Essentially, it integrates the area under the bell curve up to the specified `z`-score.

### Examples:

1. **Basic Example**:
   To calculate the cumulative probability for a `z`-score of `1.5`:
   ```excel
   =NORMSDIST(1.5)
   ```
   Result: `0.933193`.

2. **Comparing Probabilities**:
   If you have two `z`-scores, you can calculate their cumulative probabilities:
   ```excel
   =NORMSDIST(-2)
   ```
   Result: `0.022751`.

3. **Statistical Analysis**:
   Use the function to find the probability below a specific `z`-score, such as `0`:
   ```excel
   =NORMSDIST(0)
   ```
   Result: `0.5`.

### Notes:

- **Standard Normal Assumption**:
    - This function assumes a normal distribution with `mean = 0` and `standard deviation = 1`. For other distributions,
      use `NORMDIST`.
- **Accuracy**:
    - The function is highly accurate for statistical purposes and outputs a value between `0` and `1`, as probabilities
      must fall within this range.
- **Limitations**:
    - Very large or very small `z`-scores may result in values extremely close to `1` or `0`, respectively, which may
      have precision limitations in some software environments.

### Applications:

- **Statistical Analysis**
    - Determine probabilities associated with standard normal distribution.
    - Compare `z`-scores or calculate the percentage of data below/above a specific value.

- **Risk Management**
    - Identify boundaries for critical risks based on pre-defined `z`-score thresholds.

- **Quality Control**
    - Determine how far a specific measurement deviates from the center of a controlled process.

### Key Differences from NORMDIST:

While `NORMSDIST` specifically operates on a standard normal distribution (`mean = 0`, `standard deviation = 1`), the
`NORMDIST` function allows for calculations on a custom normal distribution with a given mean and standard deviation.

> **Tip**: Use `NORMSDIST` when working specifically with standard normal distributions, such as when evaluating
statistical z-scores.