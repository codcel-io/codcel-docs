<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMLOG2 Function

The `IMLOG2` function in Excel calculates the base-2 logarithm of a complex number. It is particularly useful in
scenarios where logarithmic transformations in base 2 are required for complex numbers, such as binary-based
computations in engineering, science, or mathematics.

### Key Features of IMLOG2:

- Computes the base-2 logarithm (`log2`) of complex numbers.
- Accepts complex numbers in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary part.
- Returns the result as a complex number in the same format: `c+di`.

### Syntax:

```plaintext
IMLOG2(inumber)
```

- **inumber**: The complex number for which you want to calculate the base-2 logarithm. This input can be:
    - A text string such as `"3+4i"`.
    - A reference to a cell containing a valid complex number.
    - Created using the `COMPLEX(real_num, imaginary_num)` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the base-2 logarithm is calculated as:

```plaintext
log2(a+bi) = log2(|z|) + i * (θ / ln(2))
```

Where:

- **|z|** is the magnitude of the complex number, i.e., `|z| = √(a² + b²)`.
- **θ** is the phase angle of the complex number, i.e., `θ = atan(b/a)` (the arctangent of `b/a`).
- The result is expressed in the form of `c+di`, where:
    - **c = log2(|z|)** is the base-2 logarithm of the magnitude.
    - **d = θ / ln(2)** is the phase angle divided by the natural logarithm of 2.

### Examples:

1. **Base-2 Logarithm of a Complex Number**:  
   `=IMLOG2("1+2i")`  
   For the complex number `1+2i`, the result is:  
   **Result**: ~`1.160964047 + 1.597036375i`

2. **Logarithm of a Purely Real Positive Number**:  
   `=IMLOG2(8)`  
   For the real number `8`, the result is:  
   **Result**: `3` (since `log2(8) = 3` and the phase angle is `0`)

3. **Logarithm of a Purely Real Negative Number**:  
   `=IMLOG2(-8)`  
   For the real number `-8`, the result is:  
   **Result**: `3 + πi / ln(2)` (~`3 + 4.532360142i`)

4. **Logarithm of Zero**:  
   `=IMLOG2(0)`  
   **Result**: Produces an error (`#NUM!`) because the logarithm of zero is undefined.

5. **Using a Reference for a Complex Input**:  
   If cell `A1` contains `"2+3i"`, then:  
   `=IMLOG2(A1)`  
   **Result**: ~`1.234969 + 1.002813i`

### Notes:

- The `IMLOG2` function handles both real and imaginary components. When the input is purely real, the result
  simplifies accordingly.
- If **inumber** is invalid or not recognized as a valid complex number, Excel will return a `#VALUE!` error.
- Use the `COMPLEX` function to create a valid complex input. For example: `=COMPLEX(4, 5)` provides the equivalent of
  `4+5i`.

### Applications:

- **Engineering**: Useful for binary logarithmic transformations in signal processing and communication systems.
- **Mathematics**: Solves equations and analyzes models requiring base-2 logarithms for complex values.
- **Computer Science**: Assists in binary-based scaling or magnitude analysis of complex datasets.
- **Data Science**: Enables logarithmic transformations for datasets involving complex numbers in base-2 computations.

### Related Functions:

- **IMLN**: Calculates the natural logarithm of a complex number.  
  Example: `=IMLN("1+2i")` → `0.804718956 + 1.107148718i`
- **IMLOG10**: Computes the base-10 logarithm of a complex number.  
  Example: `=IMLOG10("1+2i")` → `0.349485002 + 0.480828578i`
- **IMEXP**: Calculates the exponential of a complex number.  
  Example: `=IMEXP("1+2i")` → `-1.131204383 + 2.471726672i`
- **COMPLEX**: Creates a complex number from real and imaginary components.  
  Example: `=COMPLEX(3, 4)` → `3+4i`

### Summary:

The `IMLOG2` function is an essential Excel tool for performing base-2 logarithmic transformations involving complex
numbers. It ensures accurate computations in a variety of scientific, mathematical, and engineering contexts, making it
a versatile function for dealing with logarithmic scales in binary systems.