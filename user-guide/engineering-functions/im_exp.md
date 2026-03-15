<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMEXP Function

The `IMEXP` function in Excel calculates the exponential of a complex number. This function is useful in mathematical,
engineering, and scientific applications where computations involving exponential growth in the complex domain are
required.

### Key Features of IMEXP:

- Performs the exponential operation on complex numbers.
- Accepts complex numbers in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary part.
- Returns the result as a complex number in the same format: `c+di`.

### Syntax:

```plaintext
IMEXP(inumber)
```

- **inumber**: The complex number for which you want to calculate the exponential. This can be:
    - A text string such as `"3+4i"`.
    - A reference to a cell containing a valid complex number.
    - Created using the `COMPLEX(real_num, imaginary_num)` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the exponential is calculated as:

```plaintext
e^(a+bi) = e^a * (cos(b) + sin(b)i)
```

Where:

- **a** is the real part of the complex number.
- **b** is the imaginary part of the complex number.
- `e^a` is the base of the natural logarithm raised to the power of `a`.
- The result is expressed in the form of `c+di`, where `c` and `d` are the real and imaginary parts, respectively.

### Examples:

1. **Exponential of a Complex Number**:  
   `=IMEXP("1+2i")`  
   For the complex number `1+2i`, the result is:  
   **Result**: ~`-1.131204383 + 2.471726672i`

2. **Exponential of a Purely Real Number**:  
   `=IMEXP(2)`  
   For the real number `2`, the result is:  
   **Result**: ~`7.389056099` (which is `e^2`)

3. **Exponential of a Purely Imaginary Number**:  
   `=IMEXP("0+πi")`  
   For the imaginary number `πi`, the result involves Euler's formula:  
   **Result**: `-1` (since `e^(πi) = cos(π) + i*sin(π)`)

4. **Using a Reference for a Complex Input**:  
   If cell `A1` contains `"2-3i"`, then:  
   `=IMEXP(A1)`  
   **Result**: ~`-7.315110095+1.042743656i`

### Notes:

- If **inumber** is `0`, the function will simply return `1` (since `e^0 = 1`).
- Numbers with very large or very small exponents may lead to computational limitations or inaccuracies.
- Use the `COMPLEX` function if you want to construct a valid complex number for input. For example:  
  `=COMPLEX(1, 2)` provides the equivalent of `1+2i`.

### Applications:

- **Electrical Engineering**: Models AC signals with exponentially varying amplitudes.
- **Mathematics**: Useful for solving differential equations and problems involving exponential growth in the complex
  domain.
- **Physics**: Handles wavefunctions and quantum mechanics calculations.
- **Data Science**: Applies to advanced machine learning techniques requiring exponential transformations in complex
  systems.

### Related Functions:

- **IMLN**: Calculates the natural logarithm of a complex number.  
  Example: `=IMLN("1+2i")` → `0.804718956 + 1.107148718i`
- **IMLOG10**: Computes the base-10 logarithm of a complex number.  
  Example: `=IMLOG10("2+3i")` → `0.349485002 + 0.477464829i`
- **IMLOG2**: Computes the base-2 logarithm of a complex number.  
  Example: `=IMLOG2("3+4i")` → `1.609640474 + 0.643501109i`
- **IMPOWER**: Raises a complex number to a given power.  
  Example: `=IMPOWER("1+1i", 2)` → `0+2i`

### Summary:

The `IMEXP` function is a powerful tool for computing the exponential of complex numbers in Excel, making it an
essential feature for advanced modelling and computations in mathematics and engineering. Its applications extend to
domains requiring precise handling of exponential growth or oscillatory behaviors in the complex plane.