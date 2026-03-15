<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## F.DIST Function

The `FDIST` (or `F.DIST` in newer versions of Excel) function calculates values for the **F-distribution**, which is a
continuous probability distribution. The F-distribution is extensively used in statistical analysis, particularly in *
*variance analysis (ANOVA)**, to compare the variances between two data sets or to test hypotheses about the equality of
variances.

The F-distribution is asymmetric and ranges from 0 to infinity. It is defined by two degrees of freedom, one associated
with the numerator and the other with the denominator.

### Key Features of F.DIST:

- Computes probabilities or cumulative probabilities for the F-distribution.
- Used to model **variances and their ratios**, particularly in hypothesis testing and ANOVA.
- Can calculate both **probability density function (PDF)** and **cumulative distribution function (CDF)** values.
- Essential for statistical applications comparing group variances or analyzing relationships in regression models.

### Syntax:

```plaintext
F.DIST(x, degrees_freedom1, degrees_freedom2, cumulative)
```

- **x**: The value at which the distribution is evaluated. It represents the ratio of variances.
- **degrees_freedom1**: The numerator degrees of freedom of the data set (positive integer).
- **degrees_freedom2**: The denominator degrees of freedom of the data set (positive integer).
- **cumulative**: Logical value indicating whether to calculate the CDF or PDF of the F-distribution:
    - `TRUE`: Calculates the cumulative probability (CDF), which gives the area under the distribution curve from 0 to
      `x`.
    - `FALSE`: Returns the probability density (PDF), which evaluates the point probability density at `x`.

### Examples:

1. `=F.DIST(2.5, 5, 10, TRUE)`  
   Calculates the cumulative probability for the F-distribution with numerator degrees of freedom = 5, denominator
   degrees of freedom = 10, and `x = 2.5`.  
   **Result**: A value between 0 and 1 giving the cumulative probability (e.g., 0.8364, depending on the input).

2. `=F.DIST(3, 6, 15, FALSE)`  
   Computes the probability density for the F-distribution with numerator degrees of freedom = 6, denominator degrees of
   freedom = 15, and `x = 3`.  
   **Result**: A positive value representing the point density (e.g., 0.0893).

3. `=F.DIST(A1, 4, 12, TRUE)`  
   Calculates the cumulative distribution for the value in cell `A1` with numerator degrees of freedom = 4 and
   denominator degrees of freedom = 12.  
   **Result**: A probability value up to the given point for the specified degrees of freedom.

### Notes:

- If `x` is negative, `F.DIST` returns an error (`#NUM!`). Only positive values of `x` are valid.
- If either `degrees_freedom1 <= 0` or `degrees_freedom2 <= 0`, the function will return an error (`#NUM!`).
- Cumulative probabilities (`cumulative=TRUE`) give the integral of the F-distribution from 0 to the given `x` value.
- Point probabilities (`cumulative=FALSE`) return values calculated from the formula of the F-distribution's PDF.
- The F-distribution requires degrees of freedom to be whole numbers, as they represent sample sizes minus certain
  constraints.

> **Tip**: Use the `F.DIST` function in statistical workflows, such as testing variance hypotheses in regression models
or performing ANOVA. Correctly specifying `degrees_freedom1` and `degrees_freedom2` is critical to ensure meaningful
results.