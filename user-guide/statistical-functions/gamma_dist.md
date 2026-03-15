<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GAMMADIST Function

The `GAMMADIST` function in Excel is used to calculate the **Gamma distribution** for a given set of values. The Gamma
distribution is widely used in statistics and probability to model variables that are skewed and non-negative, such as
waiting times in a queuing system.

### Key Features of GAMMADIST:

- It computes the cumulative probability or probability density of a variable based on the Gamma distribution.
- It supports both cumulative distribution and probability density functions depending on the input settings.
- Commonly used in statistical analysis, particularly for modeling non-negative continuous variables.

### Syntax:

```plaintext
GAMMADIST(x, alpha, beta, cumulative)
```

- **x**: The value at which you want to evaluate the Gamma distribution. Must be ≥ 0.
- **alpha**: The shape parameter of the Gamma distribution. Must be > 0.
- **beta**: The scale parameter of the Gamma distribution. Must be > 0.
- **cumulative**: A logical value (TRUE/FALSE) that specifies the type of Gamma distribution to return:
    - `TRUE`: Returns the cumulative distribution function.
    - `FALSE`: Returns the probability density function.

### How It Works:

1. **Probability Density Function (PDF)**: When `cumulative` is `FALSE`, `GAMMADIST` calculates the probability density
   at a specific `x` value:
   ```plaintext
   PDF = ( (x^(alpha-1)) * e^(-x/beta) ) / ( (beta^alpha) * Γ(alpha) )
   ```

2. **Cumulative Distribution Function (CDF)**: When `cumulative` is `TRUE`, `GAMMADIST` returns the probability that a
   variable will take a value less than or equal to `x`:
   ```plaintext
   CDF = ∫ (t^(alpha-1)) * e^(-t/beta) / ( (beta^alpha) * Γ(alpha) ) dt, from t=0 to x
   ```

### Examples:

1. **Basic Gamma Distribution Calculation (PDF):**

   Calculate the probability density for `x = 2`, `alpha = 3`, and `beta = 1`:
   ```excel
   =GAMMADIST(2, 3, 1, FALSE)
   ```
   Result: `0.180`.

2. **Cumulative Gamma Distribution (CDF):**

   Calculate the cumulative probability for `x = 2`, `alpha = 3`, and `beta = 1`:
   ```excel
   =GAMMADIST(2, 3, 1, TRUE)
   ```
   Result: `0.323`.

3. **Gamma Calculation with Different Scale Parameter:**

   Calculate the probability density for `x = 5`, `alpha = 2`, and `beta = 2`:
   ```excel
   =GAMMADIST(5, 2, 2, FALSE)
   ```
   Result: `0.084224`.

### Notes:

- The function requires all input parameters to meet their specified constraints (`x ≥ 0`, `alpha > 0`, and `beta > 0`).
  If any of these conditions are not satisfied, Excel returns a `#NUM!` error.
- The function uses the Gamma function (`Γ(alpha)`) internally as part of its calculations.
- The shape and scale parameters (`alpha` and `beta`) control the skewness and spread of the distribution, making it
  highly adaptable in statistical modeling.

### Applications:

- **Statistics and Probability**: Used in reliability analysis and survival models.
- **Finance**: Models duration between events, like credit defaults.
- **Engineering**: Simulates waiting times or service times in systems.
- **Research**: Fits data with non-negative skewed distributions.

> **Tip:** The `GAMMADIST` function is particularly powerful for analyzing real-world phenomena like waiting times,
> rainfall, and various time-to-failure models, making it valuable in fields ranging from economics to engineering.