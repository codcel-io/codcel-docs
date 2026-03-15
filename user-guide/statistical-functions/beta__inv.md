<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BETA.INV Function

The `BETA.INV` function in Excel calculates the **inverse of the cumulative beta probability density function** for a
given probability. In other words, it determines the value `x` such that the cumulative beta distribution function with
specified parameters equals the given probability.

This function is primarily used in statistics and probability calculations, especially when working with data modeled by
the beta distribution.

### Key Features of BETA.INV:

- Computes the value associated with a given cumulative probability for the beta distribution.
- Supports specifying bounds of the interval where the beta distribution applies (`lower_bound` and `upper_bound`).

### Syntax:

```plaintext
BETA.INV(probability, alpha, beta, [lower_bound], [upper_bound])
```

- **probability**: A numeric value between `0` and `1` that specifies the cumulative probability.
- **alpha**: Positive shape parameter of the beta distribution that determines its skewness.
- **beta**: Positive shape parameter of the beta distribution that determines its skewness.
- **[lower_bound]** (optional): The minimum value of the `x` range. Defaults to `0` if omitted.
- **[upper_bound]** (optional): The maximum value of the `x` range. Defaults to `1` if omitted.

### Examples:

1. **Basic Calculation**  
   `=BETA.INV(0.6, 2, 5)`  
   Calculates the inverse beta distribution for the cumulative probability `0.6` with `alpha = 2`, `beta = 5`, and the
   default interval `[0, 1]`.  
   **Result**: `0.428571`.

2. **Custom Boundaries**  
   `=BETA.INV(0.75, 3, 4, 0, 10)`  
   Finds the value of `x` within the interval `[0, 10]` for a cumulative probability of `0.75` with `alpha = 3` and
   `beta = 4`.  
   **Result**: `6.875`.

3. **Negative Bounds**  
   `=BETA.INV(0.2, 1, 2, -10, 0)`  
   Computes the inverse beta distribution for probability `0.2` with `alpha = 1`, `beta = 2`, over the interval
   `[-10, 0]`.  
   **Result**: `-8`.

### Notes:

- If `alpha ≤ 0`, `beta ≤ 0`, or `probability` is outside the range `[0, 1]`, the function returns an error (`#NUM!` or
  `#VALUE!`).
- If `lower_bound` and `upper_bound` are omitted, the function assumes the default interval of `[0, 1]`.
- The function is closely related to the `BETA.DIST` function but applies inversely.

> **Tip**: Use `BETA.INV` for reverse probability calculations, such as finding the threshold value corresponding to a
given cumulative probability in beta-distributed data.