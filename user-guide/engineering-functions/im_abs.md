<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMABS Function

The `IMABS` function in Excel calculates the absolute value (or modulus) of a complex number. This function is
particularly useful in fields like engineering, data analysis, and mathematics where working with complex numbers is
common.

### Key Features of IMABS:

- Calculates the **absolute value** (modulus) of a **complex number**, which represents the distance of the complex
  number from zero in the complex plane.
- The function works with complex numbers in the format `a+bi`, `a-bi`, or `a+bj`, where `a` is the real part and `b` is
  the imaginary part.
- Helps in analyzing and comparing complex numbers in numerical and graphical contexts.

### Syntax:

```plaintext
IMABS(inumber)
```

- **inumber**: The complex number for which you want to calculate the absolute value. It should be in the form of a text
  string, like `"3+4i"`, or a reference pointing to a cell that contains a complex number.

### Formula:

The formula to calculate the absolute value (modulus) of a complex number `a+bi` is:

```plaintext
√(a² + b²)
```

Where:

- **a** is the real part of the complex number.
- **b** is the imaginary part of the complex number.

### Examples:

1. **Calculate the Absolute Value of a Complex Number**:  
   `=IMABS("3+4i")`  
   For the complex number `3+4i`, the absolute value is calculated as:  
   **Result**: `5` (since `√(3² + 4²) = √(9 + 16) = √25 = 5`)

2. **Use a Reference to a Complex Number**:  
   If cell `A1` contains `"5-12i"`, then:  
   `=IMABS(A1)`  
   Calculates the absolute value of `5-12i`.  
   **Result**: `13` (since `√(5² + (-12)²) = √(25 + 144) = √169 = 13`)

3. **Absolute Value of a Purely Real Number**:  
   `=IMABS("7")`  
   For a real number, the absolute value is simply the number's magnitude.  
   **Result**: `7`

4. **Absolute Value of a Purely Imaginary Number**:  
   `=IMABS("0+6i")`  
   For a purely imaginary number, the absolute value is equal to the magnitude of the imaginary part.  
   **Result**: `6`

### Notes:

- If **inumber** is not recognized as a valid complex number, the function will return a `#NUM!` error.
- Complex numbers in Excel can be generated using the `COMPLEX` function:
  `=COMPLEX(real_num, imaginary_num)`.

### Applications:

- **Signal Processing**: Measure the magnitude of signals represented by complex numbers.
- **Electrical Engineering**: Analyze AC circuits and study impedance represented by complex numbers.
- **Data Analysis**: Compare magnitudes of datasets involving complex numbers.

### Related Functions:

- **IMAGINARY**: Returns the imaginary part of a complex number.  
  Example: `=IMAGINARY("3+4i")` → `4`
- **IMREAL**: Returns the real part of a complex number.  
  Example: `=IMREAL("3+4i")` → `3`
- **IMSUM**: Adds two or more complex numbers.  
  Example: `=IMSUM("3+4i", "1-2i")` → `4+2i`
- **IMPRODUCT**: Multiplies two or more complex numbers.  
  Example: `=IMPRODUCT("3+4i", "1-2i")` → `11-2i`

### Summary:

The `IMABS` function is an indispensable tool when working with complex numbers in mathematical, engineering, and
analytical contexts. By calculating the modulus of a complex number, it allows for a better understanding of the
magnitude and graphical representation of the number in the complex plane.