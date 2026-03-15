<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## WEIBULL.DIST Function

The `WEIBULL.DIST` function in Excel is used to **calculate the Weibull distribution**. It can return either the
probability density function (PDF) or the cumulative distribution function (CDF) of the Weibull distribution, depending
on the input parameters.

### Key Features of WEIBULL.DIST:

- **Statistical Analysis**: Commonly used in reliability analysis, failure rate modeling, and life data analysis.
- **Flexible Output**: Can calculate either cumulative distribution (for probabilities) or probability density (for
  likelihood at a specific value).
- **Shape and Scale Parameters**: The function relies on these parameters to adjust the curve of the distribution.

### Syntax:

```plaintext
WEIBULL.DIST(x, alpha, beta, cumulative)
```

- **x**: Required. The value for which you want to evaluate the function. Must be ≥ 0.
- **alpha**: Required. The shape parameter of the Weibull distribution. Must be > 0.
- **beta**: Required. The scale parameter of the Weibull distribution. Must be > 0.
- **cumulative**: Required. A logical value (TRUE or FALSE) that specifies the type of distribution to calculate:
    - `TRUE`: Returns the cumulative distribution function (CDF).
    - `FALSE`: Returns the probability density function (PDF).

### How It Works:

1. **Cumulative Distribution Function (CDF)**:
   For `cumulative = TRUE`, the function computes the probability that a random variable from the Weibull distribution
   is less than or equal to `x`:
   ```plaintext
   F(x) = 1 - e^(-(x / β)^α)
   ```

2. **Probability Density Function (PDF)**:
   For `cumulative = FALSE`, the function computes the likelihood or density at a specific value `x`:
   ```plaintext
   f(x) = (α / β) * (x / β)^(α - 1) * e^(-(x / β)^α)
   ```

Where:

- **F(x)** is the cumulative probability.
- **f(x)** is the probability density.
- **α (alpha)** is the shape parameter.
- **β (beta)** is the scale parameter.
- **e** is the base of the natural logarithm.

### Examples:

1. **Cumulative Distribution (CDF)**:
   Suppose you want to calculate the cumulative probability for `x = 5` with `alpha = 2` and `beta = 3`:
   ```excel
   =WEIBULL.DIST(5, 2, 3, TRUE)
   ```

   Result: Returns the probability that the random variable is less than or equal to 5.

2. **Probability Density (PDF)**:
   To calculate the PDF at `x = 5` with `alpha = 2` and `beta = 3`:
   ```excel
   =WEIBULL.DIST(5, 2, 3, FALSE)
   ```

   Result: Returns the likelihood of exactly 5 in the Weibull distribution.

3. **Fail-Safe Testing**:
   If you're measuring the probability of failure within a time threshold (e.g., `x = 10`), given a product lifetime
   modeled by `alpha = 1.5` and `beta = 12`, you can compute:
   ```excel
   =WEIBULL.DIST(10, 1.5, 12, TRUE)
   ```

### Comparisons with Related Functions:

- **`WEIBULL.DIST` vs `EXPON.DIST`**:
    - `WEIBULL.DIST` allows for variable shapes of the distribution with the shape parameter `alpha`.
    - `EXPON.DIST` is a specific case of the Weibull distribution where `alpha = 1`.
- **`WEIBULL.DIST` vs `NORM.DIST`**:
    - `WEIBULL.DIST` is suited for modeling time-to-failure and reliability analysis.
    - `NORM.DIST` is used for normal (Gaussian) distributions.

### Notes:

- **Input Requirements**:
    - `x` must be greater than or equal to 0.
    - `alpha` and `beta` must be positive values, otherwise, the function returns a `#NUM!` error.
- **Logical `cumulative` Input**:
    - Input can be a boolean value (`TRUE` or `FALSE`) or numeric equivalents (`1` for TRUE, `0` for FALSE).

### Applications:

- **Reliability Engineering**: Model time between failures of components or systems.
- **Risk Analysis**: Calculate probabilities of events occurring within specified ranges.
- **Lifetime Predictions**: Estimate useful life of products before failure.
- **Queuing Theory