<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMSUM Function

The `IMSUM` function in Excel adds two or more complex numbers. This function is commonly used in engineering,
mathematical, and scientific fields where operations on complex numbers are needed.

### Key Features of IMSUM:

- Performs addition between two or more complex numbers expressed in the form `a+bi` or `a+bj`.
- Handles real numbers by treating them as complex numbers with an imaginary part of `0`.
- Returns the result in a valid complex number format.

### Syntax:

```plaintext
IMSUM(inumber1, [inumber2], ...)
```

- **inumber1**: The first complex number or real number to be added. This can be:
    - A string, such as `"6+4i"`.
    - A cell reference containing a valid complex number.
    - A real number.
- **inumber2, ...**: Additional complex numbers or real numbers to add. Same input formats as `inumber1`.

### Formula Details:

Adding complex numbers involves summing their real and imaginary parts separately. For two complex numbers
`z1 = x1 + y1i` and `z2 = x2 + y2i`, the sum is:

```plaintext
z = (x1 + x2) + (y1 + y2)i
```

Excel automates this calculation and formats the result as a complex number.

### Examples:

1. **Adding Two Complex Numbers**:  
   `=IMSUM("5+3i", "2-4i")`  
   Adds `5 + 3i` and `2 - 4i`:  
   **Result**: `7 - i`

2. **Adding Real Number and Complex Number**:  
   `=IMSUM(10, "3+5i")`  
   Treats `10` as `10 + 0i` and adds to `3 + 5i`:  
   **Result**: `13 + 5i`

3. **Adding Multiple Complex Numbers**:  
   `=IMSUM("1+2i", "3+4i", "5-6i")`  
   Adds the three numbers:  
   **Result**: `9 + 0i`

4. **Using Cell References**:  
   If cell `A1` contains `"4+3i"` and cell `A2` contains `"5-7i"`, then:  
   `=IMSUM(A1, A2)`  
   Adds `4 + 3i` and `5 - 7i`:  
   **Result**: `9 - 4i`

5. **Handling Purely Real Numbers**:  
   `=IMSUM(6, 4)`  
   Adds `6` and `4`, both treated as real numbers:  
   **Result**: `10 + 0i`

6. **Adding Imaginary Numbers**:  
   `=IMSUM("0+4i", "0-3i")`  
   Adds `4i` and `-3i`:  
   **Result**: `0 + i`

### Notes:

- If any input is not formatted as a valid complex number, Excel will return a `#VALUE!` error.
- The output is always displayed in complex number format, even if the imaginary part is `0` (e.g., `4` is displayed as
  `4+0i`).

### Applications:

- **Engineering**: Useful for adding impedance or phasors in circuit analysis.
- **Mathematics**: Simplifies operations on complex numbers in algebraic equations.
- **Science**: Helps solve complex systems and models involving imaginary components.

### Related Functions:

- **IMSUB**: Subtracts one complex number from another.  
  Example: `=IMSUB("7+3i", "4+5i")` → `3 - 2i`
- **IMPRODUCT**: Multiplies two or more complex numbers.  
  Example: `=IMPRODUCT("1+2i", "3-4i")` → `11 + 2i`
- **IMDIV**: Divides one complex number by another.  
  Example: `=IMDIV("6+8i", "3-2i")` → `0.153846154 + 2.692307692i`
- **IMSQRT**: Finds the square root of a complex number.  
  Example: `=IMSQRT("4+3i")` → `2 + 0.75i`

### Summary:

The `IMSUM` function in Excel provides a straightforward and efficient way to add complex numbers. This functionality is
essential in applications that require arithmetic with real and imaginary components, ensuring accurate computation in
various fields.