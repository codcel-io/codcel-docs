<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BESSELJ Function

The `BESSELJ` function in Excel computes the **Bessel function of the first kind**, denoted as **Jₙ(x)**. This
mathematical function is widely used in physics, engineering, and applied mathematics to solve problems involving
cylindrical or spherical symmetry, such as heat conduction, wave propagation, and vibrations.

### Key Features of BESSELJ:

- Computes the value of the **Bessel function of the first kind** for a given order (`n`).
- Specifically computes **Jₙ(x)**:
    - `x` is the input value.
    - `n` is the order of the function, representing the degree of the Bessel function.
- Commonly used in contexts involving solutions to certain differential equations.

### Syntax:

```plaintext
BESSELJ(x, n)
```

- **x**: The input value at which the Bessel function is evaluated.
    - Must be a numeric value (real number).
- **n**: The order of the Bessel function (must be a whole number).
    - Represents the degree of the function.
    - If `n` is not an integer, Excel truncates it to the nearest integer.

### Examples:

1. **Basic Example**:  
   `=BESSELJ(2, 3)`  
   Computes the Bessel function of the first kind for `x = 2` and `n = 3`.  
   **Result**: `0.128943249` (approximate value).

2. **Zero Order Calculation**:  
   `=BESSELJ(1, 0)`  
   Calculates the Bessel function of the first kind for `x = 1` and `n = 0`.  
   **Result**: `0.765197687` (approximate value).

3. **Negative Input for x**:  
   `=BESSELJ(-3, 2)`  
   Computes the Bessel function for `x = -3` and `n = 2`.  
   **Result**: `-0.486091260` (approximate value).

### Notes:

- **Behavior of BESSELJ**:
    - The Bessel function of the first kind oscillates, producing sinusoidal-like results for certain values of `x`.
- **Truncation of n**:
    - The order `n` must be a whole number (integer); Excel automatically truncates non-integer values.
- **Error values**:
    - `#NUM!`: Returned when input values are out of a valid range or invalid for certain computations.
    - `#VALUE!`: Returned if `x` or `n` is non-numeric.

### Applications:

- **Use Case**: The `BESSELJ` function is frequently used in scientific applications where solutions to problems
  involving cylindrical or spherical coordinates are required, such as in acoustics, electromagnetics, and fluid
  mechanics.