<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NORMSINV Function

The `NORMSINV` function in Excel is used to calculate the **inverse of the standard normal cumulative distribution**.
This function returns the value (z-score) associated with a given probability in the standard normal distribution, which
has a mean of 0 and a standard deviation of 1.

### Key Features of NORMSINV:

- Computes the z-value corresponding to a specified cumulative probability for the standard normal distribution.
- Useful for statistical analyses, hypothesis testing, or any scenario where you need to transform a probability back
  into a z-score.
- The updated equivalent function in modern Excel is `NORM.S.INV`.

### Syntax:

```plaintext
NORMSINV(probability)
```

- **probability**: A probability value between **0 and 1** (non-inclusive), representing the area under the standard
  normal curve to the left of the desired z-value.

### Example:

1. **Finding the z-score for a given probability**  
   Suppose you want to find the z-score where the cumulative probability is **0.95**:  
   Formula:  
   `=NORMSINV(0.95)`  
   **Result**: The function returns approximately **1.645**, which is the z-score that corresponds to the 95th
   percentile of the standard normal distribution.

### Notes:

- **Output**:
    - The result is a numerical value (z-score) that can be positive or negative, depending on the input probability.
    - Higher probabilities produce positive z-scores (to the right of the mean), while lower probabilities produce
      negative z-scores (to the left of the mean).
- **Invalid inputs**:
    - If the `probability` argument is ≤ 0 or ≥ 1, the function returns a `#NUM!` error as these probabilities are
      invalid for a standard normal distribution.
- The `NORMSINV` function is equivalent to the `NORM.INV` function when the mean is 0 and standard deviation is 1 (i.e.,
  the standard normal form).

### Use Cases:

- **Hypothesis Testing**: Determine critical values (z-scores) for a given significance level in hypothesis testing.
- **Confidence Intervals**: Calculate the z-scores required for constructing confidence intervals.
- **Probability-Score Conversion**: Convert cumulative probabilities into corresponding values in normal distribution
  analysis.

> **Note**: The `NORMSINV` function is still supported for backward compatibility but has been replaced by the
`NORM.S.INV` function in modern Excel versions, which provides improved naming consistency.