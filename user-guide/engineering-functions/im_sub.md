<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMSUB Function

The `IMSUB` function in Excel subtracts one complex number from another. This function is useful in mathematical,
engineering, and scientific fields where complex number computations are required.

### Key Features of IMSUB:

- Performs subtraction between two complex numbers expressed in the form `a+bi` or `a+bj`.
- Handles real numbers, treating them as complex numbers with an imaginary part of `0`.
- Returns the result as a valid complex number.

### Syntax:

```plaintext
IMSUB(inumber1, inumber2)
```

- **inumber1**: The complex number or real number from which `inumber2` is subtracted. This can be:
    - A string, such as `"5+3i"`.
    - A cell reference containing a valid complex number.
    - A real number.
- **inumber2**: The complex number or real number to subtract from `inumber1`. Same input formats as `inumber1`.

### Formula Details:

The subtraction of two complex numbers `z1 = x1 + y1i` and `z2 = x2 + y2i` results in a new complex number
`z = (x1 - x2) + (y1 - y2)i`. Excel automates this calculation and provides the result directly.

### Examples:

1. **Subtracting Two Complex Numbers**:  
   `=IMSUB("8+5i", "3+2i")`  
   Subtracting `3 + 2i` from `8 + 5i`:  
   **Result**: `5 + 3i`

2. **Real Number Minus Complex Number**:  
   `=IMSUB(10, "4+6i")`  
   Treats `10` as `10+0i` and subtracts `4+6i`:  
   **Result**: `6 - 6i`

3. **Complex Number Minus Real Number**:  
   `=IMSUB("7+2i", 3)`  
   Treats `3` as `3+0i` and subtracts:  
   **Result**: `4 + 2i`

4. **Using Cell References**:  
   If cell `A1` contains `"6+3i"` and cell `A2` contains `"4+5i"`, then:  
   `=IMSUB(A1, A2)`  
   Subtracts `4+5i` from `6+3i`:  
   **Result**: `2 - 2i`

5. **Handling Purely Imaginary Numbers**:  
   `=IMSUB("0+5i", "0-3i")`  
   Subtracts `-3i` from `5i`:  
   **Result**: `0 + 8i`

6. **Subtracting Identical Numbers**:  
   `=IMSUB("6-2i", "6-2i")`  
   Subtracts `6-2i` from itself:  
   **Result**: `0`

### Notes:

- If either input is not formatted as a valid complex number, Excel will return a `#VALUE!` error.
- Outputs are always expressed in complex number format, even if the imaginary part is `0` (e.g., `4` → `4+0i`).

### Applications:

- **Engineering**: Useful for analyzing systems involving impedance or phasor calculations.
- **Mathematics**: Simplifies algebraic operations on complex numbers.
- **Science**: Helps solve equations and models involving complex numbers.

### Related Functions:

- **IMSUM**: Adds two or more complex numbers.  
  Example: `=IMSUM("3+2i", "4-5i")` → `7 - 3i`
- **IMSQRT**: Calculates the square root of a complex number.  
  Example: `=IMSQRT("4+9i")` → `2.581988897 + 1.742396482i`
- **IMMULT**: Multiplies two complex numbers.  
  Example: `=IMMULT("1+2i", "3-4i")` → `11 + 2i`
- **IMDIV**: Divides one complex number by another.  
  Example: `=IMDIV("7+6i", "4+3i")` → `2 - i`

### Summary:

The `IMSUB` function in Excel provides a straightforward and efficient method for subtracting complex numbers. Whether
for engineering, mathematics, or scientific applications, it ensures accurate subtraction in complex number systems.