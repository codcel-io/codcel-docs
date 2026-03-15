<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORMINV Function

The `NORMINV` function in Excel is used to **calculate the inverse of the cumulative normal distribution** for a given
probability. It essentially finds the `x` value (data point) such that the cumulative normal distribution equals the
provided probability.

### Key Features of NORMINV:

- *Inverse of cumulative distribution*: It allows you to determine the value of a random variable in a normal
  distribution corresponding to a given probability.
- Useful for scenarios where you need to calculate threshold values, percentiles, or z-scores based on a normal
  distribution.

### Syntax:

```plaintext
NORMINV(probability, mean, standard_dev)
```

- **probability**: Required. The probability corresponding to the normal distribution you are analyzing. This value must
  be between `0` and `1` (exclusive).
- **mean**: Required. The mean (average) of the normal distribution.
- **standard_dev**: Required. The standard deviation of the normal distribution (must be positive).

### How It Works:

The `NORMINV` function computes the value `x` such that the cumulative distribution function (CDF) of the normal
distribution equals the given probability. In essence, it solves the reverse of the `NORM.DIST` function.

The formula for the CDF is:

```plaintext
CDF = (1 / (standard_dev * SQRT(2 * PI))) * Integrate[ EXP(-(t - mean)^2 / (2 * standard_dev^2)) ] from -∞ to x
```

The `NORMINV` function finds the corresponding `x`.

### Examples:

1. **Basic Example**:
   To find the value corresponding to the 90th percentile in a normal distribution with a mean of `50` and a standard
   deviation of `10`:
   ```excel
   =NORMINV(0.9, 50, 10)
   ```
   Result: `62.815515`.

2. **Real-Life Scenario**:
   A company’s employees are rated based on a normal distribution with a mean performance score of `70` and a standard
   deviation of `15`. To find the score threshold that determines the top 5% of employees:
   ```excel
   =NORMINV(0.95, 70, 15)
   ```
   Result: `94.674788`.

3. **Application for Thresholds**:
   If you want to find the cut-off value for students scoring below the bottom 10% in an exam with a mean score of `80`
   and a standard deviation of `12`:
   ```excel
   =NORMINV(0.1, 80, 12)
   ```
   Result: `64.635143`.

### Notes:

- **Input Validation**:
    - **`probability`** must be between `0` and `1`. If it is `0`, `1`, or any value outside this range, the function
      returns `#NUM!`.
    - **`standard_dev`** must be greater than `0`. If it is `0` or negative, the function returns `#NUM!`.
    - Non-numeric inputs return `#VALUE!`.

- **Understanding Outputs**:
    - Small probabilities (close to `0`) correspond to values far below the mean in the distribution.
    - Probabilities near `1` correspond to values far above the mean.

- **Replaced by NORM.INV**:
    - In Excel 2010 and later versions, the `NORMINV` function was replaced by `NORM.INV`, which has identical
      functionality.

### Applications:

- **Statistical Tasks**: Calculate z-scores or threshold values to partition a dataset based on probabilities.
- **Finance**: Determine the value of a metric (e.g., return rate) corresponding to a specific percentile or
  probability.
- **Quality Control**: Find the specification limits or control limits in processes based on probabilities.
- **Risk Management**: Identify boundaries for data values based on a pre-defined risk probability.

> **Tip**: Use `NORMINV` when you have a known distribution and probability and need to calculate an exact value. For a
> modern version of this function, use `NORM.INV` in Excel 2010 or later.
> **NOTE**: The implementation is the same as NORM.INV