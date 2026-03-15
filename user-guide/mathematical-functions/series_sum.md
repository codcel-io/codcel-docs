<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SERIESSUM(x, n, m, coefficients)

- **x**: The input value at which the power series is evaluated. Typically, this is a numeric value.
- **n**: The initial power to which `x` is raised.
- **m**: The step by which the power increases in each term of the series.
- **coefficients**: An array or range of numeric values that are multiplied by the respective powers of `x`.

### Description:

The `SERIESSUM` function calculates the sum of a power series based on the input value `x`, the initial power `n`, the
step `m`, and the provided `coefficients`. The power series is defined as:

    SERIESSUM(x, n, m, coefficients) = c1 * (x^n) + c2 * (x^(n + m)) + c3 * (x^(n + 2*m)) + ... 

Where `c1`, `c2`, ... are the values in the `coefficients` array.

### Examples:

1. `=SERIESSUM(2, 1, 1, {1, 2, 3})`  
   This will calculate `1*(2^1) + 2*(2^2) + 3*(2^3)`, which equals `2 + 8 + 24 = 34`.

2. `=SERIESSUM(0.5, 0, 1, {1, 3, 5})`  
   This will calculate `1*(0.5^0) + 3*(0.5^1) + 5*(0.5^2)`, which equals `1 + 1.5 + 1.25 = 3.75`.

3. `=SERIESSUM(3, 2, 2, {2, 4})`  
   This will calculate `2*(3^2) + 4*(3^4)`, which equals `18 + 324 = 342`.

### Notes:

- The `coefficients` array must be a valid range or an array constant (e.g., `{1, 2, 3}`).
- If the `coefficients` array is empty, `SERIESSUM` will return `0`.
- Ensure the input for `x`, `n`, `m`, and the `coefficients` are numeric; otherwise, the function may return a `#VALUE!`
  error.
- This function is particularly useful in evaluating polynomial approximations or truncated infinite series like Taylor
  series.