<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BESSELY Function

The `BESSELY` function in Excel computes the **Bessel function of the second kind**, denoted as **Yₙ(x)**.  
This mathematical function arises in solving differential equations with cylindrical symmetry in various scientific  
and engineering applications, such as acoustic wave propagation, electromagnetics, and vibration analysis.

### Key Features of BESSELY:

- Computes the value of the **Bessel function of the second kind** for a given order (`n`).
- Specifically computes **Yₙ(x)**:
    - `x` is the input value (must be greater than zero).
    - `n` is the order of the function, representing the degree of the Bessel function.
- It is often used to model problems involving cylindrical symmetry where boundary conditions  
  require a second independent solution (compared to the Bessel function of the first kind).

### Syntax:

```plaintext
BESSELY(x, n)
```

- **x**: The input value at which the Bessel function is evaluated.
    - Must be a numeric value **greater than 0**.
- **n**: The order of the Bessel function.
    - Must be a numeric value. If a non-integer value is provided, Excel truncates it to the nearest integer.

### Examples:

1. **Basic Example**:  
   `=BESSELY(2, 0)`  
   Computes the Bessel function of the second kind for `x = 2` and `n = 0`.  
   **Result**: `-0.5103757` (approximate value).

2. **Higher Order Calculation**:  
   `=BESSELY(3, 2)`  
   Computes the Bessel function of the second kind for `x = 3` and `n = 2`.  
   **Result**: `-0.1289432` (approximate value).

3. **Smaller Value of x**:  
   `=BESSELY(0.5, 1)`  
   Evaluates the Bessel function for `x = 0.5` and `n = 1`.  
   **Result**: `-1.4714724` (approximate value).

### Notes:

- **Behavior of BESSELY**:
    - The Bessel function of the second kind, **Yₙ(x)**, is singular (undefined) at `x = 0`.
    - Larger values of `n` cause the function to oscillate more rapidly.
    - Used as a companion to the **Bessel function of the first kind** (`BESSELJ`), forming a complete set of linearly
      independent solutions to Bessel's differential equation.
- **Error values**:
    - `#VALUE!`: Occurs if `x` or `n` is non-numeric.
    - `#NUM!`: Occurs if `x` is less than or equal to zero (invalid input for this function).
- **Truncation of n**:
    - The order `n` must be a whole number; Excel truncates non-integer values automatically.

### Applications:

- **Use Case**: The `BESSELY` function is widely used in **wave equations** and **vibration analysis** for cylindrical
  structures,  
  including calculations in structural mechanics, acoustics, and fluid dynamics.

- **Complementary to BESSELJ**: The `BESSELY` function complements the Bessel function of the first kind (**Jₙ(x)**),  
  particularly when a second independent solution is needed for modeling wave behavior in physics.