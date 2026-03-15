<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GAMMALN Function

The `GAMMALN` function in Excel is used to calculate the **natural logarithm of the Gamma function** for a given number.
This function is often used in statistical and mathematical computations where the Gamma function plays a central role,
particularly in probability distributions and factorial approximations for non-integer values.

### Key Features of GAMMALN:

- Computes the natural logarithm of the Gamma function, which is useful when the direct computation of the Gamma
  function produces numbers that are too large to handle accurately.
- Aids in simplifying complex formulas in probability and statistics, such as those involving Beta or Gamma
  distributions.
- Commonly applied in scenarios involving factorial approximations, combinatorics, and statistical distributions.

### Syntax:

```plaintext
GAMMALN(number)
```

- **number**: The input for which the natural logarithm of the Gamma function is calculated. Must be greater than 0.

### How It Works:

The `GAMMALN` function returns the natural logarithm of the Gamma value, denoted mathematically as:

```plaintext
GAMMALN(number) = ln(Γ(number))
```

Here, `Γ(number)` is the Gamma function, which generalizes the factorial function such that:

```plaintext
Γ(n) = (n-1)! for integer n > 0
```

For non-integer values, the Gamma function extends the factorial concept continuously.

### Examples:

1. **Basic Calculation**:

   Calculate the natural logarithm of `Γ(5)`:
   ```excel
   =GAMMALN(5)
   ```
   Result: `3.1781` (equivalent to `ln(4!)` or `ln(24)`).

2. **Non-Integer Example**:

   Compute the natural logarithm of `Γ(2.5)`:
   ```excel
   =GAMMALN(2.5)
   ```
   Result: `0.2847`.

3. **Large Input**:

   Calculate the logarithm for a large argument to avoid direct computation of the Gamma function:
   ```excel
   =GAMMALN(10)
   ```
   Result: `12.8018`.

### Notes:

- **Parameter Constraints**:
    - The input `number` must be positive (`number > 0`).
    - If `number <= 0`, Excel returns a `#NUM!` error.

- This function is particularly useful to avoid computational overflow or inaccuracies when working with very large
  factorial-like expressions or probability distributions.

- `GAMMALN.PRECISE` is an updated, more accurate version of this function introduced in newer versions of Excel. For
  compatibility, use it wherever possible.

### Applications:

- **Statistical Modeling**: Simplify Gamma or Beta distribution calculations.
- **Probabilistic Analysis**: Used in log-probability computations to handle large values.
- **Combinatorics**: Evaluate logarithms of large factorial-like terms for binomial coefficient approximations.
- **Data Science**: Handle large data or model probabilities efficiently without numerical overflow.

> **Tip:** Use `GAMMALN` when dealing with factorials for large or fractional values, especially in fields like
> statistics, machine learning, and risk analysis.