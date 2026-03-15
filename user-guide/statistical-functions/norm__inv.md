<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORM.INV Function

The `NORM.INV` function in Excel is used to **calculate the inverse of the normal cumulative distribution** for a
specified probability, mean, and standard deviation. In other words, it returns the value `x` such that the cumulative
distribution function of the normal distribution equals a given probability.

### Key Features of NORM.INV:

- Converts a **probability value** from the cumulative normal distribution back into a corresponding `x` value.
- Useful for statistical analysis, such as determining threshold values or z-scores for a specific probability level.

### Syntax:

```plaintext
NORM.INV(probability, mean, standard_dev)
```

- **probability**: Required. The cumulative probability for which you want to find the corresponding `x` value.
- **mean**: Required. The mean (average) of the normal distribution.
- **standard_dev**: Required. The standard deviation of the normal distribution.

### How It Works:

The function computes the value of `x` using the inverse of the cumulative normal distribution function. For a given
cumulative probability, it determines the corresponding data point in the normal distribution characterized by the
specified mean and standard deviation.

### Examples:

1. **Basic Example**:
   To find the value of `x` such that the cumulative probability is `0.95` for a normal distribution with a mean of `50`
   and standard deviation of `10`:
   ```excel
   =NORM.INV(0.95, 50, 10)
   ```
   Result: `66.448`.

2. **Real-Life Scenario**:
   Assume test scores in an exam follow a normal distribution with a mean of `75` and a standard deviation of `15`. To
   find the score corresponding to the top 5% of students (95th percentile):
   ```excel
   =NORM.INV(0.95, 75, 15)
   ```
   Result: `99.674`.

### Notes:

- **Input Validation**:
    - The `probability` parameter must be between `0` and `1`. Otherwise, the function will return a `#NUM!` error.
    - If `mean` or `standard_dev` are non-numeric, the function returns a `#VALUE!` error.
    - A `standard_dev` value of `0` or negative will result in a `#NUM!` error.

- **Output Ranges**:
    - The output value depends on the distribution parameters. For probabilities close to `0` or `1`, the `x` value may
      approach extreme values.

### Applications:

- **Statistical Analysis**: Use `NORM.INV` to compute thresholds or determine cutoff points for specific percentiles
  within a dataset.
- **Finance**: Estimate risk thresholds or calculate value-at-risk (VaR) in portfolio analysis.
- **Quality Control**: Identify process limits for reaching a given defect probability.
- **Education**: Determine exam score cutoffs corresponding to certain percentile ranks.

> **Tip**: The `NORM.INV` function replaced the older `NORMINV` function starting with Excel 2010 to align with other
statistical functions.

> **NOTE**: The implementation is the same as NORMINV 