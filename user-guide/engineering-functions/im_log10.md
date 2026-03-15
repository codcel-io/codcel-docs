<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMLOG10 Function

The `IMLOG10` function in Excel calculates the base-10 logarithm of a complex number. This function is particularly
useful in engineering, scientific, and mathematical contexts where logarithmic transformations involving complex numbers
are needed.

### Key Features of IMLOG10:

- Computes the base-10 logarithm (`log10`) of complex numbers.
- Accepts complex numbers in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary part.
- Returns the result as a complex number in the same format: `c+di`.

### Syntax:

```plaintext
IMLOG10(inumber)
```

- **inumber**: The complex number for which you want to calculate the base-10 logarithm. This input can be:
    - A text string such as `"3+4i"`.
    - A reference to a cell containing a valid complex number.
    - Created using the `COMPLEX(real_num, imaginary_num)` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the base-10 logarithm is calculated as:

```plaintext
log10(a+bi) = log10(|z|) + i * (θ / ln(10))
```

Where:

- **|z|** is the magnitude of the complex number, i.e., `|z| = √(a² + b²)`.
- **θ** is the phase angle of the complex number, i.e., `θ = atan(b/a)` (the arctangent of `b/a`).
- The result is expressed in the form of `c+di`, where:
    - **c = log10(|z|)** is the base-10 logarithm of the magnitude.
    - **d = θ / ln(10)** is the phase angle divided by the natural logarithm of 10.

### Examples:

1. **Base-10 Logarithm of a Complex Number**:  
   `=IMLOG10("1+2i")`  
   For the complex number `1+2i`, the result is:  
   **Result**: ~`0.349485002 + 0.480828578i`

2. **Logarithm of a Purely Real Positive Number**:  
   `=IMLOG10(10)`  
   For the real number `10`, the result is:  
   **Result**: `1` (since `log10(10) = 1` and the phase angle is `0`)

3. **Logarithm of a Purely Real Negative Number**:  
   `=IMLOG10(-10)`  
   For the real number `-10`, the result is:  
   **Result**: `1 + πi / ln(10)` (~`1 + 1.364376353i`)

4. **Logarithm of Zero**:  
   `=IMLOG10(0)`  
   **Result**: Produces an error (`#NUM!`) because the logarithm of zero is undefined.

5. **Using a Reference for a Complex Input**:  
   If cell `A1` contains `"2+3i"`, then:  
   `=IMLOG10(A1)`  
   **Result**: ~`0.349485 + 0.563615i`

### Notes:

- The `IMLOG10` function handles both real and imaginary components. When the input is purely real, the result
  simplifies accordingly.
- If **inumber** is invalid or not recognized as a complex number, Excel will return a `#VALUE!` error.
- Use the `COMPLEX` function to create a valid complex input. For example: `=COMPLEX(4, 5)` provides the equivalent of
  `4+5i`.

### Applications:

- **Engineering**: Analysis of signal magnitudes and phase shifts in systems using a logarithmic scale.
- **Mathematics**: Solves equations and models involving base-10 logarithms of complex numbers.
- **Physics**: Assists in complex wave analysis and logarithmic scaling in acoustics or energy computations.
- **Data Science**: Supports transformations of complex data sets into meaningful logarithmic scales.

### Related Functions:

- **IMLN**: Calculates the natural logarithm of a complex number.  
  Example: `=IMLN("1+2i")` → `0.804718956 + 1.107148718i`
- **IMLOG2**: Computes the base-2 logarithm of a complex number.  
  Example: `=IMLOG2("1+2i")` → `1.160964047 + 1.597036375i`
- **IMEXP**: Calculates the exponential of a complex number.  
  Example: `=IMEXP("0.349485002+0.480828578i")` → `1+2i`
- **IMPOWER**: Raises a complex number to a power.  
  Example: `=IMPOWER("1+2i", 3)` → `-11+2i`

### Summary:

The `IMLOG10` function is an essential Excel tool for performing logarithmic transformations involving complex numbers.
It allows for precise computations in a variety of scientific, mathematical, and engineering domains, ensuring
compatibility with base-10 logarithms in the complex number space.