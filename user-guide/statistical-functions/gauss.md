<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GAUSS Function

The `GAUSS` function in Excel is used to compute the probability that a random variable from a **standard normal
distribution** (mean = 0, standard deviation = 1) will fall between 0 and a specified value. It is commonly employed in
probability theory and statistical applications.

### Key Features of GAUSS:

- Calculates the probability under the normal distribution curve from 0 up to the specified value.
- Assumes a standard normal distribution with:
    - Mean (`μ`) = 0.
    - Standard Deviation (`σ`) = 1.
- Useful in statistical and probability-related computations involving normalized scores or Z-scores.
- Provides a cumulative probability computation directly.

### Syntax:

```plaintext
GAUSS(z)
```

- **z**: The specified value for which you want the cumulative distribution probability from 0.

### How It Works:

The `GAUSS` function computes the cumulative probability under the standard normal distribution curve between 0 and the
input `z` value. It is mathematically expressed as:

```plaintext
GAUSS(z) = N(z) - 0.5
```

Here, `N(z)` represents the cumulative distribution function (CDF) for a standard normal distribution. Subtracting 0.5
adjusts the result to exclude the lower half of the distribution (below 0), as the standard normal distribution is
symmetric about `0`.

For negative `z` values, the result represents the **negative cumulative probability** from 0 to `z`.

### Examples:

1. **Basic Calculation**:

   Compute the probability for a `z` value of `1.5`:
   ```excel
   =GAUSS(1.5)
   ```
   Result: `0.4332` (meaning 43.32% of the data lies between 0 and `1.5` under a standard normal distribution).

2. **Negative Z-Score**:

   Compute the probability for a `z` value of `-2`:
   ```excel
   =GAUSS(-2)
   ```
   Result: `-0.4772` (negative indicates cumulative probability is below 0).

3. **Large Z-Score**:

   Compute the probability for a `z` value of `3`:
   ```excel
   =GAUSS(3)
   ```
   Result: `0.4986` (almost all the data from 0 to `z` is included).

### Notes:

- **Parameter Constraints**:
    - Input `z` can be any real number.
    - Large positive or negative values for `z` approach cumulative probabilities of `0.5` or `-0.5`, respectively, due
      to the distribution's nature.

- The `GAUSS` function complements other statistical functions, such as `NORM.DIST` or `NORM.S.DIST`, but simplifies
  probability calculations for the symmetric standard normal distribution.

### Applications:

- **Risk Analysis**: Helps estimate probabilities within specific ranges based on Z-scores.
- **Statistical Inference**: Provides quick cumulative probabilities for hypothesis testing or confidence intervals.
- **Data Analysis**: Facilitates evaluation of standard normal data or results from Z-transformations.

> **Tip:** Use `GAUSS` for simple standard normal probability computations and combine it with other distribution
functions for more complex scenarios.