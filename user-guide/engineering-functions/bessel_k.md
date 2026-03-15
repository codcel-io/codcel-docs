<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BESSELK Function

The `BESSELK` function in Excel computes the **Modified Bessel function of the second kind**, denoted as **Kₙ(x)**.  
This mathematical function is used in various fields, such as physics, engineering, and applied mathematics—  
specifically in solving problems involving cylindrical or spherical symmetry under certain conditions, including  
those with exponential decay behavior like heat transfer, diffusion, and electromagnetic wave propagation.

### Key Features of BESSELK:

- Computes the value of the **Modified Bessel function of the second kind** for a given order (`n`).
- Specifically computes **Kₙ(x)**:
    - `x` is the input value (must be greater than zero).
    - `n` is the order of the function, representing the degree of the Bessel function.
- It is commonly used in situations that involve modified cylindrical functions and when exponential decay is present  
  in solutions to differential equations.

### Syntax:

```plaintext
BESSELK(x, n)
```

- **x**: The input value at which the Bessel function is evaluated.
    - Must be a numeric value **greater than 0**.
- **n**: The order of the Bessel function.
    - Must be a numeric value. If a non-integer is provided, Excel truncates it to the nearest integer.

### Examples:

1. **Basic Example**:  
   `=BESSELK(2, 3)`  
   Computes the Modified Bessel function of the second kind for `x = 2` and `n = 3`.  
   **Result**: `0.01794001` (approximate value).

2. **Zero Order Calculation**:  
   `=BESSELK(1, 0)`  
   Calculates the Modified Bessel function of the second kind for `x = 1` and `n = 0`.  
   **Result**: `0.421024438` (approximate value).

3. **Larger Value of x**:  
   `=BESSELK(5, 2)`  
   Computes the Bessel function for `x = 5` and `n = 2`.  
   **Result**: `0.046308506` (approximate value).

### Notes:

- **Behavior of BESSELK**:
    - Unlike the Bessel function of the first kind, the Modified Bessel function of the second kind does not oscillate.
    - It decays exponentially as `x` increases (large values of `x`) and grows significantly in magnitude for small `x`.
- **Error values**:
    - `#VALUE!`: Occurs if `x` or `n` is non-numeric.
    - `#NUM!`: Occurs if `x` is less than or equal to zero (invalid input for this function).
- **Truncation of n**:
    - The order `n` must be a whole number; Excel truncates non-integer values automatically.

### Applications:

- **Use Case**: The `BESSELK` function is often employed in scientific and engineering calculations where  
  exponential decay with cylindrical or spherical symmetry is modeled.  
  Practical applications include analyzing heat conduction, diffusion processes, and wave transmission.