<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORM.S.INV Function

The `NORM.S.INV` function in Excel is used to **return the inverse of the standard normal cumulative distribution**.  
It finds the z-score corresponding to a given probability value under the standard normal distribution (mean of 0 and
standard deviation of 1).

### Key Features of NORM.S.INV:

- Returns the z-score (number of standard deviations from the mean) for a given probability.
- Useful in statistics, hypothesis testing, and probability analysis.

### Syntax:

```plaintext
NORM.S.INV(probability)
```

- **probability**: Required. A probability associated with the standard normal distribution. This value must be between
  `0` and `1` (exclusive).

### How It Works:

The `NORM.S.INV` function is essentially the inverse of the cumulative probability function for the **standard normal
distribution**.

For example:

- A probability of `0.5` corresponds to a z-score of `0` (since the distribution is symmetric about the mean).
- A smaller probability (e.g., `0.025`) will correspond to a negative z-score (e.g., `-1.96`), indicating a value below
  the mean.
- A larger probability (e.g., `0.975`) will correspond to a positive z-score (e.g., `1.96`), indicating a value above
  the mean.

### Examples:

1. **Find the Z-Score for 95% Probability**:
   To calculate the z-score for a probability of `0.95`:
   ```excel
   =NORM.S.INV(0.95)
   ```
   Result: `1.644854` (approximately).

2. **Central Probability**:
   For a probability of `0.5` (the center of the standard normal distribution):
   ```excel
   =NORM.S.INV(0.5)
   ```
   Result: `0` (mean of the standard normal distribution).

3. **Lower Tail**:
   Calculate the z-score for the `2.5%` lower tail probability:
   ```excel
   =NORM.S.INV(0.025)
   ```
   Result: `-1.959964` (approximately).

4. **Large Tail Probability**:
   For a cumulative probability of `0.999`:
   ```excel
   =NORM.S.INV(0.999)
   ```
   Result: `3.090232` (approximately).

### Notes:

- **Input Validation**:
    - If `probability` is not between `0` and `1` (inclusive of boundaries), the function returns `#NUM!`.
    - If `probability` is non-numeric, the function returns `#VALUE!`.

- **Symmetry Property**:
    - The function reflects the symmetry of the standard normal distribution. For example:
      ```plaintext
      =NORM.S.INV(0.975) = 1.96, and =NORM.S.INV(0.025) = -1.96
      ```

### Applications:

- **Confidence Interval Calculations**:
  Use `NORM.S.INV` to find critical z-values for constructing confidence intervals in hypothesis testing.

- **Risk Assessment**:
  Determine thresholds or cut-offs in predictive models based on probabilities.

- **Excel Charts with Normal Distribution**:
  Use the z-scores returned by `NORM.S.INV` to mark specific points or percentiles on a visual representation of the
  standard normal distribution.

> **Tip**: Combine `NORM.S.INV` with other distribution functions (e.g., `NORM.DIST` or `NORM.INV`) to work with
non-standard normal distributions.
> **Note**: This is the same as NORMSINV