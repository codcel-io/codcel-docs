<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GAMMAINV Function

The `GAMMAINV` function in Excel is used to calculate the **inverse of the Gamma cumulative distribution** for a given
probability. This function is often used in statistical analysis to find the value of a variable corresponding to a
specific probability under the Gamma distribution.

### Key Features of GAMMAINV:

- It calculates the value `x` such that the cumulative Gamma distribution up to `x` equals a given probability.
- Useful for scenarios where you need to determine a threshold or critical value based on a probability.
- Commonly applied in statistical and probability models to assess outcomes for skewed and non-negative variables.

### Syntax:

```plaintext
GAMMAINV(probability, alpha, beta)
```

- **probability**: The probability associated with the Gamma distribution. Must be between 0 and 1 (exclusive).
- **alpha**: The shape parameter of the Gamma distribution. Must be > 0.
- **beta**: The scale parameter of the Gamma distribution. Must be > 0.

### How It Works:

The `GAMMAINV` function returns the value `x` for which the Gamma cumulative distribution function (CDF) equals the
specified `probability`. Mathematically, it's the solution to the equation:

```plaintext
P(X ≤ x) = probability
```

Where `X` follows the Gamma distribution parameterized by `alpha` and `beta`.

### Examples:

1. **Basic Inverse Calculation**:

   Find the value of `x` such that the cumulative probability is `0.6` for a Gamma distribution with `alpha = 3` and
   `beta = 2`:
   ```excel
   =GAMMAINV(0.6, 3, 2)
   ```
   Result: `5.48`.

2. **Critical Value Calculation**:

   Determine the critical value `x` for a cumulative probability of `0.9` given `alpha = 4` and `beta = 1.5`:
   ```excel
   =GAMMAINV(0.9, 4, 1.5)
   ```
   Result: `9.85`.

3. **Threshold Example**:

   For a process with `alpha = 2.5` and `beta = 3`, calculate the value `x` where the cumulative distribution equals
   `0.25`:
   ```excel
   =GAMMAINV(0.25, 2.5, 3)
   ```
   Result: `3.87`.

### Notes:

- **Parameter Constraints**:
    - The input probability must satisfy `0 < probability < 1`.
    - Shape and scale parameters (`alpha` and `beta`) must be positive.

- If constraints are not met, Excel returns a `#NUM!` error for invalid inputs.

- Inverse Gamma computations involve iterative numerical techniques, making them computationally intensive for very
  large or very small probabilities.

### Applications:

- **Reliability Testing**: Identify time thresholds for cumulative failure probabilities.
- **Project Management**: Assess thresholds for non-negative task durations.
- **Risk Assessment**: Determine critical points for probabilities in models involving waiting times or financial risks.
- **Research & Analytics**: Analyze thresholds at specific confidence levels in datasets with variable skewness.

> **Tip:** The `GAMMAINV` function is especially valuable when setting thresholds based on probabilities in fields such
> as operations research, finance, and reliability engineering.