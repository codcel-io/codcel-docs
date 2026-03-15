<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GAMMA.INV Function

The `GAMMA.INV` function in Excel is used to calculate the **inverse of the Gamma cumulative distribution function** for
a given probability and specified parameters. It is commonly applied in statistics when you need to find the value of
`x` such that the cumulative distribution function equals a desired probability.

### Key Features of GAMMA.INV:

- Used to determine threshold values in Gamma-distributed data.
- Helps solve for `x` in scenarios where you know the cumulative probability (area under the curve).
- Often applied in statistical modeling and data analysis.

### Syntax:

```plaintext
GAMMA.INV(probability, alpha, beta)
```

- **probability**: A numeric value between `0` and `1` that represents the cumulative probability.
- **alpha**: The shape parameter of the Gamma distribution. Must be > 0.
- **beta**: The scale parameter of the Gamma distribution. Must be > 0.

### How It Works:

The `GAMMA.INV` function calculates the value of `x` such that:

```plaintext
P(X ≤ x) = probability
```

Where:

- `P(X ≤ x)` is the cumulative probability.
- `α` (alpha) is the shape parameter.
- `β` (beta) is the scale parameter.
- The computation uses the inverse of the Gamma distribution's cumulative formula.

### Examples:

1. **Simple Example:**

   Find the value of `x` such that the cumulative probability equals `0.8`, with `alpha = 2` and `beta = 1`:

   ```excel
   =GAMMA.INV(0.8, 2, 1)
   ```
   Result: `3.218875...`

   This means that at `x = 3.218875`, the cumulative probability is `0.8`.

2. **Changing Parameters:**

   Find `x` for a cumulative probability of `0.4`, with `alpha = 3` and `beta = 2`:

   ```excel
   =GAMMA.INV(0.4, 3, 2)
   ```
   Result: `4.087456...`

3. **Using Extreme Probabilities:**

   Find `x` for very small probabilities like `0.01`, with `alpha = 5` and `beta = 1`:

   ```excel
   =GAMMA.INV(0.01, 5, 1)
   ```
   Result: `1.624169...`

### Notes:

- **Probability Value**: Must be between 0 and 1 (inclusive). If it is outside this range, Excel will return a `#NUM!`
  error.
- **Alpha and Beta Parameters**: Both `alpha` and `beta` must be greater than 0. If they are less than or equal to 0,
  Excel will return a `#NUM!` error.
- If the input values are invalid, Excel may return a `#VALUE!` or `#NUM!` error.

### Applications:

- **Statistical Analysis**: Widely used to find threshold or cutoff values in modeling Gamma distributions.
- **Risk Assessment**: Helpful when calculating values corresponding to certain risk levels or confidence intervals.
- **Engineering and Science**: Used for probabilistic simulations or reliability analysis.

> **Tip:** Use `GAMMA.INV` alongside other statistical functions like `GAMMA.DIST` to create complete models for
understanding Gamma-distributed data or conducting probability-based analyses.