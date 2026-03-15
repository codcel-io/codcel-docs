<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMCONJUGATE Function

The `IMCONJUGATE` function in Excel returns the **complex conjugate** of a given complex number. The complex conjugate
of a number is derived by reversing the sign of its imaginary part while keeping the real part unchanged. This function
is frequently used in fields like mathematics, engineering, and physics for complex number operations involving symmetry
and conjugation.

### Key Features of IMCONJUGATE:

- Returns the **complex conjugate** of a complex number.
- Works with complex numbers in the form `a+bi`, `a-bi`, or `a+bj`, where `a` is the real part and `b` is the imaginary
  part.
- Useful for simplifying complex arithmetic and finding the magnitude of complex numbers.

### Syntax:

```plaintext
IMCONJUGATE(inumber)
```

- **inumber**: The complex number for which you want to calculate the complex conjugate. It should either be a text
  string like `"3+4i"`, or a reference pointing to a cell containing the complex number.

### Formula:

Given a complex number `a+bi`, the complex conjugate is calculated as:

```plaintext
a-bi
```

Where:

- **a** is the real part of the complex number.
- **b** is the imaginary part of the complex number.

### Examples:

1. **Calculate the Complex Conjugate**:  
   `=IMCONJUGATE("3+4i")`  
   For the complex number `3+4i`, the conjugate is:  
   **Result**: `3-4i`

2. **Use a Reference to a Complex Number**:  
   If cell `A1` contains `"5-12i"`, then:  
   `=IMCONJUGATE(A1)`  
   Returns the conjugate of `5-12i`.  
   **Result**: `5+12i`

3. **Conjugate of a Purely Real Number**:  
   `=IMCONJUGATE("7")`  
   For a purely real number, the conjugate is the number itself (since the imaginary part is `0`):  
   **Result**: `7`

4. **Conjugate of a Purely Imaginary Number**:  
   `=IMCONJUGATE("0+6i")`  
   For a purely imaginary number, the conjugate is:  
   **Result**: `0-6i`

### Notes:

- If **inumber** is not a valid complex number, the function returns a `#NUM!` error.
- Complex numbers in Excel can be created using the `COMPLEX` function:
  ```plaintext
  =COMPLEX(real_num, imaginary_num)
  ```
  For example, `=COMPLEX(3, 4)` creates the complex number `3+4i`.
- The complex conjugate is especially useful in calculating the magnitude of a complex number:
  ```plaintext
  |z| = SQRT(IMPRODUCT(z, IMCONJUGATE(z)))
  ```

### Applications:

- **Mathematics**: Used in simplifying fractions involving complex numbers and solving quadratic equations.
- **Engineering**: Helps in computations involving phasors and impedances in AC circuit analysis.
- **Physics**: Useful in wave mechanics and quantum theory.

### Related Functions:

- **IMABS**: Returns the absolute value (magnitude) of a complex number.  
  Example: `=IMABS("3+4i")` → `5`
- **IMREAL**: Returns the real part of a complex number.  
  Example: `=IMREAL("3+4i")` → `3`
- **IMAGINARY**: Returns the imaginary part of a complex number.  
  Example: `=IMAGINARY("3+4i")` → `4`
- **IMARGUMENT**: Returns the argument (angle in radians) of a complex number.  
  Example: `=IMARGUMENT("3+4i")` → `0.93`

### Summary:

The `IMCONJUGATE` function is an essential tool for working with complex numbers in Excel. By calculating the complex
conjugate, it provides a convenient method for performing operations such as simplifying expressions and calculating
magnitudes. Its utility spans multiple fields including mathematics, engineering, and physics, making it an
indispensable function for handling complex number computations.