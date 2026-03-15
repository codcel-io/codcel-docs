<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMPRODUCT Function

The `IMPRODUCT` function in Excel multiplies two or more complex numbers. It is useful in mathematical, engineering, and
scientific applications involving complex number arithmetic, such as signal processing, electrical circuit analysis, and
mathematical transformations.

### Key Features of IMPRODUCT:

- Multiplies complex numbers in the form `a+bi` or `a+bj`, where `a` represents the real part and `b` represents the
  imaginary part.
- Accepts multiple arguments, allowing multiplication of more than two complex numbers.
- Returns the result in complex number format: `c+di`.

### Syntax:

```plaintext
IMPRODUCT(inumber1, [inumber2], ...)
```

- **inumber1, [inumber2], ...**: The complex numbers to be multiplied. Each value can be:
    - A string, such as `"3+2i"`.
    - A cell reference containing a valid complex number.
    - Generated using the `COMPLEX(real_num, imaginary_num)` function.
    - A real number (for cases where the imaginary part is `0`).

### Formula and Calculation:

For complex numbers `z1 = a+bi` and `z2 = c+di`, their product is calculated as:

```plaintext
z1 * z2 = (a*c - b*d) + (a*d + b*c)i
```

Where:

- The real part of the product is calculated as `(a*c - b*d)`.
- The imaginary part of the product is calculated as `(a*d + b*c)`.

### Examples:

1. **Multiplying Two Complex Numbers**:  
   `=IMPRODUCT("3+4i", "1-2i")`  
   For the numbers `3+4i` and `1-2i`, the result is:  
   **Result**: `11-2i`

2. **Multiplying a Complex Number by a Real Number**:  
   `=IMPRODUCT("2+3i", 5)`  
   Multiplies `2+3i` by `5` (a real number with no imaginary part):  
   **Result**: `10+15i`

3. **Multiplying Real Numbers**:  
   `=IMPRODUCT(3, 4)`  
   Multiplies the real numbers `3` and `4`:  
   **Result**: `12` (no imaginary part).

4. **Multiplying More Than Two Numbers**:  
   `=IMPRODUCT("1+2i", "3-4i", "2+0i")`  
   Multiplies three numbers:  
   **Result**: `-22+6i`

5. **Using Cell References**:  
   If cell `A1` contains `"2+3i"` and cell `A2` contains `"4-5i"`, then:  
   `=IMPRODUCT(A1, A2)`  
   **Result**: `23+2i`

6. **Multiplying a Complex Number by Zero**:   
   `=IMPRODUCT("2-3i", 0)`  
   Multiplying any number by zero results in:  
   **Result**: `0`

### Notes:

- If any of the inputs (**inumber**) is not a valid complex number or is in an incorrect format, Excel will return a
  `#VALUE!` error.
- The function supports multiplication of both real and imaginary numbers seamlessly.
- The order of multiplication does not affect the result (commutative property of multiplication).

### Applications:

- **Engineering**: Used in designing and analyzing systems involving complex impedance and signals.
- **Physics**: Assists in calculations of wave properties and resonance.
- **Data Analysis**: Helps in transformations and manipulations involving multidimensional datasets.
- **Mathematics**: Solves and simplifies polynomial equations with complex roots.

### Related Functions:

- **IMSUM**: Adds two or more complex numbers.  
  Example: `=IMSUM("2+3i", "1+4i")` → `3+7i`
- **IMSUB**: Subtracts one complex number from another.  
  Example: `=IMSUB("2+3i", "1-4i")` → `1+7i`
- **IMDIV**: Divides one complex number by another.  
  Example: `=IMDIV("3+4i", "1+2i")` → `2-1i`
- **IMABS**: Returns the magnitude (absolute value) of a complex number.  
  Example: `=IMABS("3+4i")` → `5`

### Summary:

The `IMPRODUCT` function provides an efficient way to multiply complex numbers in Excel. It is an essential tool for
handling mathematical calculations, electrical system analysis, and other advanced applications that require complex
arithmetic. Its ability to handle multiples inputs, both real and imaginary, makes it versatile and highly functional.