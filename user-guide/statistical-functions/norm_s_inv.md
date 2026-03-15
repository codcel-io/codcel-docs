<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORMSINV Function

The `NORMSINV` function in Excel is used to **calculate the inverse of the standard normal cumulative distribution** for
a given probability. It determines the z-score (standardized value) such that the cumulative standard normal
distribution equals the given probability.

### Key Features of NORMSINV:

- *Inverse of the standard normal distribution*: It calculates the value in a standard normal distribution that
  corresponds to a given cumulative probability.
- Assumes a standard normal distribution with a mean of `0` and a standard deviation of `1`.
- Frequently used in statistics for z-score calculations, hypothesis testing, and confidence interval estimation.

### Syntax:

```plaintext
NORMSINV(probability)
```

- **probability**: Required. The cumulative probability for which you want to find the corresponding z-score. This value
  must be between `0` and `1` (exclusive).

### How It Works:

The `NORMSINV` function works with the **standard normal distribution**, which is a normal distribution with the
following properties:

- Mean: `0`
- Standard Deviation: `1`

The function determines the z-score (value along the standard normal curve) such that the cumulative probability up to
that z-score equals the specified `probability`.

In mathematical terms, it finds the value `z` satisfying:

```plaintext
P(Z ≤ z) = probability
```

Where `Z` is a random variable following a standard normal distribution.

### Examples:

1. **Basic Example**:
   To calculate the z-score where 90% of the values lie below it in a standard normal distribution:
   ```excel
   =NORMSINV(0.9)
   ```
   Result: `1.281552`.

2. **Find the z-score for a 5% left-tail probability**:
   If you need a z-score corresponding to the lowest 5% in the standard normal curve:
   ```excel
   =NORMSINV(0.05)
   ```
   Result: `-1.644854`.

3. **Application in Testing**:
   When conducting a hypothesis test and you need the z-score for a significance level of 0.025 (two-tailed test):
   ```excel
   =NORMSINV(0.975)
   ```
   Result: `1.959964`.

4. **Confidence Interval**:
   For a 99% confidence interval, find z-scores for cumulative probabilities 0.005 and 0.995:
   ```excel
   =NORMSINV(0.005)  // Lower z-score
   =NORMSINV(0.995)  // Upper z-score
   ```
   Results: `-2.575829` and `2.575829`.

### Notes:

- **Input Validation**:
    - The `probability` must be strictly between `0` and `1`. If it's `0`, `1`, or outside this range, the function
      returns `#NUM!`.
    - Non-numeric inputs result in `#VALUE!`.

- **Relationship to NORMINV**:
    - Unlike the `NORMINV` function, the `NORMSINV` function assumes a standard normal distribution (mean `0`, standard
      deviation `1`) and does not require additional parameters.

- **Output Behavior**:
    - Small probabilities (close to `0`) map to large negative z-scores.
    - Probabilities near `1` map to large positive z-scores.

### Applications:

- **Statistical Analysis**: Convert probabilities into z-scores for standard normal distributions.
- **Hypothesis Testing**: Determine critical z-scores for given significance levels.
- **Confidence Intervals**: Calculate z-scores for confidence levels in sampling or estimation methods.
- **Finance**: Derive standardized returns or percentiles for risk analysis.

> **Tip**: Use `NORMSINV` when dealing with probabilities in the standard normal distribution. For normal distributions
> with a different mean or standard deviation, use `NORMINV` or `NORM.INV` in Excel.
> **Note**: This is the same as NORM.S.INV