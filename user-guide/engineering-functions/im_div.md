<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMDIV Function

The `IMDIV` function in Excel calculates the **quotient** resulting from the division of two complex numbers. It is
designed for operations involving complex numbers, represented in the form `a+bi` or `a+bj`, where `a` is the real part
and `b` is the imaginary part.

This function is particularly useful in mathematical and engineering applications that require precise division in the
complex domain.

### Key Features of IMDIV:

- Performs division of one complex number by another.
- Accepts inputs as text strings (e.g., `"a+bi"`), cell references containing complex numbers, or results from the
  `COMPLEX` function.
- Returns the result as a complex number in the form `c+di`.

### Syntax:

```plaintext
IMDIV(inumber1, inumber2)
```

- **inumber1**: The complex number you want to divide (the numerator). This can be:
    - A text string such as `"3+4i"`.
    - A reference to a cell containing a valid complex number.
    - Created using the `COMPLEX(real_num, imaginary_num)` function.
- **inumber2**: The complex number you want to divide by (the denominator). This follows the same rules as `inumber1`.

### Formula and Calculation:

For two complex numbers `z1 = a+bi` and `z2 = c+di`, the division is calculated as follows:

```plaintext
z1 / z2 = [(a * c + b * d) + (b * c - a * d)i] / (c^2 + d^2)
```

Where:

- **a** and **b** are the real and imaginary parts of `z1` (numerator).
- **c** and **d** are the real and imaginary parts of `z2` (denominator).
- The denominator of the result is `c^2 + d^2`.

### Examples:

1. **Division of Two Complex Numbers**:  
   `=IMDIV("3+4i", "1+2i")`  
   For the complex numbers `3+4i` (numerator) and `1+2i` (denominator), this returns:  
   **Result**: ~`2.2 - 0.4i`

2. **Using a Reference for a Complex Denominator**:  
   If cell `A1` contains `"5+3i"`, then:  
   `=IMDIV("4+2i", A1)`  
   Result of dividing `4+2i` by `5+3i`:  
   **Result**: ~`0.588235294 + 0.05882352941i`

3. **Division of a Real Number by a Complex Number**:  
   `=IMDIV(5, "2+3i")`  
   When dividing a real number (e.g., `5`) by a complex number, the result is:  
   **Result**: ~`0.7692307692 - 1.1538461538i`

4. **Division of a Complex Number by a Real Number**:  
   `=IMDIV("6-8i", 2)`  
   Dividing a complex number by a real number is straightforward:  
   **Result**: `3-4i`

### Notes:

- If **inumber2** (denominator) is `0` or has both the real and imaginary parts as `0`, the function will return a
  `#NUM!` error.
- The function ensures that results are returned in valid complex number notation.
- Use `COMPLEX(real_num, imaginary_num)` to create complex numbers easily in Excel. For example:  
  `=COMPLEX(4, -5)` creates the complex number `4-5i`.

### Applications:

- **Electrical Engineering**: Calculates impedances and voltage-current ratios in AC circuits involving impedance.
- **Mathematics**: Solves equations and models involving division in the complex plane.
- **Data Science**: Useful for advanced computations requiring complex numbers or polar coordinates.

### Related Functions:

- **IMSUM**: Adds complex numbers.  
  Example: `=IMSUM("3+4i", "5-2i")` → `8+2i`
- **IMSUB**: Subtracts one complex number from another.  
  Example: `=IMSUB("6+5i", "2+1i")` → `4+4i`
- **IMPRODUCT**: Multiplies two or more complex numbers.  
  Example: `=IMPRODUCT("3+2i", "4-3i")` → `18+i`
- **IMCONJUGATE**: Returns the conjugate of a complex number.  
  Example: `=IMCONJUGATE("4+5i")` → `4-5i`

### Summary:

The `IMDIV` function is an essential part of Excel's complex number toolkit, enabling precise division for advanced
applications across mathematics, engineering, and data analysis. By performing division in the complex plane, it
provides professionals and researchers with a powerful tool for accurate and efficient calculations.