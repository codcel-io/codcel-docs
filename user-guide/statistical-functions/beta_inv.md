<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BETAINV Function

The `BETAINV` function in Excel returns the **inverse of the beta cumulative probability density function** for a
specified probability. In simpler terms, it computes the value `x` such that
`BETADIST(x, alpha, beta, lower_bound, upper_bound)` equals the given probability.

This function is useful in statistical and probability analyses, especially when modeling data that follows a beta
distribution.

### Key Features of BETAINV:

- Requires input of probability for which you want to find the corresponding value.
- Allows flexibility in defining the boundaries (`lower_bound` and `upper_bound`) of the beta distribution.

### Syntax:

```plaintext
BETAINV(probability, alpha, beta, [lower_bound], [upper_bound])
```

- **probability**: The probability corresponding to the beta distribution. Must be between `0` and `1`.
- **alpha**: A positive parameter of the distribution that shapes the curve.
- **beta**: A positive parameter of the distribution that shapes the curve.
- **[lower_bound]** (optional): The minimum value of the interval of `x`. Defaults to `0` if omitted.
- **[upper_bound]** (optional): The maximum value of the interval of `x`. Defaults to `1` if omitted.

### Examples:

1. `=BETAINV(0.5, 2, 5)`  
   Calculates the value of `x` for the beta distribution with `alpha = 2` and `beta = 5`, assuming the interval `[0, 1]`
   by default.  
   **Result**: `0.392857`.

2. `=BETAINV(0.8, 3, 4, 0, 10)`  
   Computes the value of `x` for the beta distribution with `alpha = 3`, `beta = 4`, and interval `[0, 10]`.  
   **Result**: `6.532`.

3. `=BETAINV(0.25, 1, 1, -5, 5)`  
   Calculates the value of `x` for a uniform beta distribution (`alpha = beta = 1`) with interval `[-5, 5]`.  
   **Result**: `-2.5`.

### Notes:

- If any of the arguments `alpha ≤ 0`, `beta ≤ 0`, or `probability` is not between `0` and `1`, the function returns an
  error (`#NUM!` or `#VALUE!`).
- The function is closely related to the `BETADIST` function but works inversely.
- When `lower_bound` and `upper_bound` are omitted, the beta distribution is applied to the standard range `[0, 1]`.

> **Tip**: Use `BETAINV` when performing reverse beta distribution calculations, particularly for solving statistical
problems involving probability thresholds.