<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BESSELI Function

The `BESSELI` function in Excel computes the **modified Bessel function of the first kind**, denoted as **Iₙ(x)**. This
mathematical function is commonly used in engineering, physics, and related fields to solve problems involving
cylindrical or spherical symmetry, particularly in wave propagation, heat conduction, and similar applications.

### Key Features of BESSELI:

- Computes the value of the modified Bessel function for a given order (n).
- Specifically computes **Iₙ(x)**, where:
    - `x` is the input value.
    - `n` is the order of the function, representing the degree of the Bessel function.
- Used commonly in scenarios requiring solutions to differential equations with cylindrical symmetry.

### Syntax:

```plaintext
BESSELI(x, n)
```

- **x**: The input value at which the Bessel function is evaluated.
    - Must be a numeric value (real value).
- **n**: The order of the Bessel function (must be a whole number).
    - Represents the degree of the modified function.
    - If `n` is not an integer, Excel truncates it to the nearest integer.

### Examples:

1. **Basic Example**:
   `=BESSELI(2, 3)`  
   This calculates the modified Bessel function of the first kind for `x = 2` and `n = 3`.  
   **Result**: `1.590636854` (approximate value).

2. **Calculating with Negative x**:
   `=BESSELI(-3, 2)`  
   This calculates the modified Bessel function for `x = -3` and `n = 2`.  
   Note that for BESSELI, the result will always be non-negative regardless of whether `x` is positive or negative.  
   **Result**: `4.880792588` (approximate value).

3. **Zero Order Calculation**:
   `=BESSELI(1, 0)`  
   Computes the value of the modified Bessel function for `x = 1` and `n = 0`.  
   **Result**: `1.266065878` (approximate value).

### Notes:

- **Behavior of BESSELI**:
    - For large `x`, the result of the BESSELI function grows exponentially.
    - The value is always **non-negative**, even if `x` is negative.
- **Truncation of n**:
    - The order `n` must be a whole number (integer), and Excel automatically truncates non-integer values.
- **Error values**:
    - `#NUM!`: Occurs when the input values are out of the allowable range (e.g., very large or invalid negative values
      in certain cases).
    - `#VALUE!`: Occurs if `x` or `n` are non-numeric.

### Applications:

- **Use Case**: The `BESSELI` function is widely used in various scientific computations, such as signal processing,
  heat transfer, and other differential equation problems where cylindrical symmetry plays a role.