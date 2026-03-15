<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMAGINARY Function

The `IMAGINARY` function in Excel extracts the imaginary part of a complex number. This function is particularly useful
in managing and analyzing data involving complex numbers in mathematical, engineering, or technical contexts.

### Key Features of IMAGINARY:

- Extracts the **imaginary part** of a **complex number**, which is the coefficient of the imaginary unit `i` or `j`.
- Works with complex numbers in the format `a+bi`, `a-bi`, `a+bj`, or `a-bj`, where `i` or `j` represents the imaginary
  unit.
- Useful for analyzing and decomposing complex numbers into their real and imaginary components.

### Syntax:

```plaintext
IMAGINARY(inumber)
```

- **inumber**: The complex number from which you want to extract the imaginary part. It should be in the form of a text
  string (e.g., `"3+4i"`), or a reference pointing to a cell containing a complex number.

### Examples:

1. **Extract Imaginary Part of a Complex Number**:  
   `=IMAGINARY("3+4i")`  
   For the complex number `3+4i`, the imaginary part is:  
   **Result**: `4`

2. **Use a Reference to a Complex Number**:  
   If cell `A1` contains `"5-12i"`, then:  
   `=IMAGINARY(A1)`  
   Extracts the imaginary part of `5-12i`.  
   **Result**: `-12`

3. **Imaginary Part of a Purely Imaginary Number**:  
   `=IMAGINARY("0+6i")`  
   For a purely imaginary number, the result is the magnitude of the imaginary part:  
   **Result**: `6`

4. **Imaginary Part of a Real Number**:  
   `=IMAGINARY("7")`  
   For a purely real number, the imaginary part is `0`, as no imaginary component exists.  
   **Result**: `0`

### Notes:

- The function returns only the **imaginary part** of a complex number and ignores the real part.
- If **inumber** is not recognized as a valid complex number, the function will return a `#NUM!` error.
- You can generate complex numbers using the `COMPLEX` function:  
  `=COMPLEX(real_num, imaginary_num)`  
  For example, `=COMPLEX(3, 4)` returns `"3+4i"`.

### Applications:

- **Signal Processing**: Analyze signals where the imaginary part represents phase or amplitude information.
- **Electrical Engineering**: Decompose impedances or voltages into their real and imaginary components.
- **Mathematics**: Work with datasets involving complex numbers by separating their components for further calculations.

### Related Functions:

- **IMREAL**: Returns the real part of a complex number.  
  Example: `=IMREAL("3+4i")` → `3`
- **IMABS**: Calculates the absolute value (modulus) of a complex number.  
  Example: `=IMABS("3+4i")` → `5`
- **IMSUM**: Adds two or more complex numbers.  
  Example: `=IMSUM("3+4i", "1-2i")` → `4+2i`
- **IMPRODUCT**: Multiplies two or more complex numbers.  
  Example: `=IMPRODUCT("3+4i", "1-2i")` → `11-2i`

### Summary:

The `IMAGINARY` function is an essential tool for working with complex numbers in Excel, allowing users to isolate and
analyze the imaginary component of complex datasets effectively.