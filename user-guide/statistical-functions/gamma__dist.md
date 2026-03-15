<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GAMMA.DIST Function

The `GAMMA.DIST` function in Excel is used to calculate the **Gamma probability density function or cumulative
distribution function** for a specified set of parameters. It is commonly used in statistics to model data that follows
a Gamma distribution.

### Key Features of GAMMA.DIST:

- Useful for modeling waiting times between events in a Poisson process.
- Supports both probability density function (PDF) and cumulative distribution function (CDF) calculations.
- Often applied in statistical analysis and probability modeling.

### Syntax:

```plaintext
GAMMA.DIST(x, alpha, beta, cumulative)
```

- **x**: The value at which to evaluate the distribution. Must be ≥ 0.
- **alpha**: The shape parameter of the Gamma distribution. Must be > 0.
- **beta**: The scale parameter of the Gamma distribution. Must be > 0.
- **cumulative**: A logical value (TRUE/FALSE) that specifies the form of the function:
    - `TRUE`: Returns the cumulative distribution function (CDF).
    - `FALSE`: Returns the probability density function (PDF).

### How It Works:

The Gamma distribution is defined using the formula:

```plaintext
f(x; α, β) = ( (x^(α-1) * e^(-x/β)) / (β^α * Γ(α)) )  for x ≥ 0
```

Where:

- `α` (alpha) is the shape parameter.
- `β` (beta) is the scale parameter.
- `Γ(α)` is the Gamma function.

### Examples:

1. **Cumulative Distribution Example:**

   Calculate the cumulative Gamma distribution for `x = 2`, `alpha = 3`, and `beta = 2`:

   ```excel
   =GAMMA.DIST(2, 3, 2, TRUE)
   ```
   Result: `0.323323...`, representing the CDF value for these parameters.

2. **Probability Density Example:**

   Calculate the probability density for `x = 2`, `alpha = 3`, and `beta = 2`:

   ```excel
   =GAMMA.DIST(2, 3, 2, FALSE)
   ```
   Result: A specific density value (`0.111565...`), representing the PDF at `x = 2`.

3. **Using Different Parameters:**

   Try a different set of parameters, such as `x = 5`, `alpha = 4`, and `beta = 1`:

   ```excel
   =GAMMA.DIST(5, 4, 1, TRUE)
   ```
   Result: `0.815263...` for the CDF.

### Notes:

- The input `x` must be a non-negative value. If `x` is less than 0, Excel will return a `#NUM!` error.
- Both `alpha` and `beta` must be greater than 0. If they are less than or equal to 0, Excel will return a `#NUM!`
  error.
- If `cumulative` is omitted, Excel may assume `FALSE` by default (PDF form).
- The Gamma distribution is closely tied to statistical applications, such as modeling times until events or analyzing
  data following an exponential distribution.

### Applications:

- **Statistical Modeling:** Widely used in statistics to model waiting times, failure rates, and other time-dependent
  phenomena.
- **Engineering and Science:** Applied in physics, reliability analysis, and biology for stochastic or probabilistic
  simulations.
- **Data Analysis:** Useful for fitting distributions to data and analyzing patterns in probability spaces.

> **Tip:** Pairing `GAMMA.DIST` with other Excel statistical functions can help in building comprehensive probability
> models and distributions. Always validate parameters (`alpha`, `beta`, `x`) for meaningful outputs.