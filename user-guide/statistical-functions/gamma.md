<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GAMMA Function

The `GAMMA` function in Excel is used to calculate the **Gamma function value** for a specified number. The Gamma
function is an advanced mathematical function often used in probability, statistics, and calculus, extending the concept
of factorials to non-integer values.

### Key Features of GAMMA:

- Calculates the Gamma value for a given number, typically for statistical or mathematical purposes.
- Extends factorial calculations to non-integer and real numbers using the formula defined for the Gamma function.
- Commonly used in areas such as probability density functions, distributions (e.g., Gamma distribution), and advanced
  modeling techniques.

### Syntax:

```plaintext
GAMMA(number)
```

- **number**: The input value for which you want to calculate the Gamma function.

### How It Works:

For a given `number` (x), the Gamma function is mathematically defined as:

```plaintext
Γ(x) = ∫ (t^(x-1)) * e^(-t) dt, from t=0 to infinity
```

In simpler terms:

- For integers (n), `GAMMA(n)` is equivalent to `(n-1)!` (factorial of n-1).
- For real and non-integer values, it calculates the continuous extension of the factorial function.

### Examples:

1. **Basic Gamma Calculation:**

   Calculate the Gamma value for an integer value (e.g., 5):
   ```excel
   =GAMMA(5)
   ```
   Result: `24`, which is equivalent to `(5-1)! = 4! = 24`.

2. **Non-Integer Gamma Calculation:**

   Calculate the Gamma value for a non-integer (e.g., 2.5):
   ```excel
   =GAMMA(2.5)
   ```
   Result: `1.329340...`, as the Gamma function extends beyond integers.

3. **Gamma Calculation for Negative Numbers:**

   Calculate the Gamma value for a negative non-integer (e.g., -1.5):
   ```excel
   =GAMMA(-1.5)
   ```
   Result: `2.363271...` (valid for most negative non-integers, although undefined for negative integers).

### Notes:

- The `number` input must be greater than 0 or a non-integer negative value. If the input is a negative integer or 0,
  Excel returns a `#NUM!` error.
- The Gamma function is closely related to statistical distributions (e.g., Chi-squared, T-distribution), making it
  highly useful in statistical and mathematical analysis.
- The function can be paired with other statistical functions like `GAMMA.DIST` for more complex probability analysis.

### Applications:

- **Statistical Modeling:** Used in probability density functions and statistical models involving the Gamma
  distribution.
- **Advanced Mathematics:** Extends factorial concepts for real and non-integer values, offering flexibility beyond
  discrete computations.
- **Engineering and Science:** Integral part of complex mathematical formulas in physics, biology, and other
  quantitative disciplines.

> **Tip:** When working with non-integer values, the `GAMMA` function provides robust results for continuous
computations and can be critical in advanced probability and statistics problems.