<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## WEIBULL Function

The `WEIBULL` function in Excel is used to **compute the Weibull probability density function or Weibull cumulative
distribution function**, which is commonly used in reliability analysis and failure rate modeling.

### Key Features of WEIBULL:

- **Versatile Distribution**: Supports:
    - **Probability Density Function (PDF)** for analyzing the likelihood of a specific outcome.
    - **Cumulative Distribution Function (CDF)** for the probability that an outcome is less than or equal to a given
      value.
- **Reliability Analysis**: Useful for assessing reliability, modeling life data, and analyzing failure rates.
- **Customizable Parameters**: Allows for tailoring the distribution with scale and shape parameters.

### Syntax:

```plaintext
WEIBULL(x, alpha, beta, cumulative)
```

- **x**: Required. The value at which to evaluate the function (must be ≥ 0).
- **alpha**: Required. The shape parameter of the Weibull distribution.
- **beta**: Required. The scale parameter of the Weibull distribution (must be > 0).
- **cumulative**: Required. A logical value:
    - **TRUE**: Computes the CDF (cumulative distribution function).
    - **FALSE**: Computes the PDF (probability density function).

### How It Works:

1. **Weibull Distribution Formula**:
    - **PDF**:
      ```plaintext
      f(x) = (alpha / beta) * (x / beta)^(alpha - 1) * EXP(-(x / beta)^alpha)
      ```
    - **CDF**:
      ```plaintext
      F(x) = 1 - EXP(-(x / beta)^alpha)
      ```

   Where:
    - `x`: The input value.
    - `alpha`: The shape parameter.
    - `beta`: The scale parameter.

2. **Parameter Implications**:
    - **alpha (shape)**:
        - Describes the behavior of the distribution:
            - `alpha > 1`: Failure rate increases over time.
            - `alpha < 1`: Failure rate decreases over time.
            - `alpha = 1`: Constant failure rate (exponential distribution).
    - **beta (scale)**:
        - Stretches or shrinks the distribution, controlling the spread of values.

3. **CDF vs PDF**:
    - **CDF (cumulative)** calculates the area under the curve up to the given value `x`.
    - **PDF (density)** returns the probability at an exact value of `x`.

### Examples:

#### 1. **Compute Weibull CDF**:

To calculate the cumulative probability up to `x = 5` using a Weibull distribution with `alpha = 2`, `beta = 3`:

```excel
=WEIBULL(5, 2, 3, TRUE)
```

- Formula used:
  ```plaintext
  F(x) = 1 - EXP(-(5 / 3)^2)
  ```
- Result indicates the probability that values are ≤ 5.

#### 2. **Compute Weibull PDF**:

To calculate the probability density at `x = 5` with the same parameters:

```excel
=WEIBULL(5, 2, 3, FALSE)
```

- Formula used:
  ```plaintext
  f(x) = (2 / 3) * (5 / 3)^(2 - 1) * EXP(-(5 / 3)^2)
  ```
- Result represents the likelihood of `x = 5`.

#### 3. **Reliability Analysis**:

In reliability analysis, you can determine the probability that a system will fail before time `x` by using:

```excel
=WEIBULL(10, 1.5, 8, TRUE)
```

This calculates the likelihood of failure within `10` time units, with specified shape and scale parameters.

### Notes:

- **Scope of Application**:
    - Reliability engineering: Life span of components, devices, etc.
    - Weather modeling: Analyzing wind speeds, rainfall, etc.
    - Risk analysis: Understanding probabilities of rare events.

- **Input Limitations**:
    - `x` must be a non-negative number.
    - `alpha` and `beta` must be positive values.
    - If invalid arguments are provided (e.g., `beta ≤ 0`), the function returns a `#NUM!` error.

- **Related Functions**:
    - Use `EXPON.DIST` for exponential distributions.
    - Use distribution tables or visualization to interpret results.

> **Tip**: Use the `WEIBULL` function for detailed probabilistic modeling, particularly in scenarios requiring
> reliability estimates or failure analysis, and feel free to adjust `alpha` and `beta` to match the context of your data!