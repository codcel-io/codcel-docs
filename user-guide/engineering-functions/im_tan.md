<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMTAN Function  

The `IMTAN` function in Excel returns the tangent of a given complex number. This function is typically used in
engineering, mathematical, and scientific fields where operations on complex numbers and trigonometric calculations are
required.

### Key Features of IMTAN:

- Calculates the tangent of a complex number expressed in the format `a+bi` or `a+bj`.
- Handles real numbers by treating them as complex numbers with an imaginary part of `0`.
- Returns the result in the form of a complex number.

### Syntax:

```plaintext
IMTAN(inumber)
```

- **inumber**: The complex number or real number for which you want to calculate the tangent. This can be:
    - A string, such as `"6+4i"`.
    - A cell reference containing a valid complex number.
    - A real number.

### Formula Details:

The tangent of a complex number `z = x + yi` is calculated as:

```plaintext
tan(z) = sin(z) / cos(z)
```

Where:

- `z` is the complex number.
- `sin(z)` and `cos(z)` are the sine and cosine of the complex number, respectively.

Excel automates these calculations and returns the result in a valid complex number format.

### Examples:

1. **Calculating the Tangent of a Complex Number**:  
   `=IMTAN("0+1i")`  
   Calculates the tangent of `1i`:  
   **Result**: `0+1.557407725i`

2. **Calculating the Tangent of a Real Number**:  
   `=IMTAN(1)`  
   Calculates the tangent of the real number `1`:  
   **Result**: `1.557407725+0i`

3. **Using a Cell Reference Containing a Complex Number**:  
   If cell `A1` contains `"3+2i"`, then:  
   `=IMTAN(A1)`  
   Calculates the tangent of `3 + 2i`:  
   **Result**: `-0.000187346+0.964760875i`

4. **Handling Purely Imaginary Numbers**:  
   `=IMTAN("0-2i")`  
   Calculates the tangent of `-2i`:  
   **Result**: `0-1.000000083i`

### Notes:

- If the input is not a valid complex number, Excel will return a `#NUM!` or `#VALUE!` error.
- IMTAN operates on both real and imaginary numbers, returning the result in complex number format. For real numbers,
  the imaginary part is always `0` (e.g., `2` is displayed as `2 + 0i`).

### Applications:

- **Engineering**: Useful for calculations involving phasors and impedance analysis.
- **Mathematics**: Assists in solving equations and problems that require the use of trigonometric functions on complex
  numbers.
- **Science**: Simplifies models and systems involving tangent calculations of imaginary and real components.

### Related Functions:

- **IMSIN**: Returns the sine of a complex number.  
  Example: `=IMSIN("1+1i")` → `1.298457581+0.634963914i`
- **IMCOS**: Returns the cosine of a complex number.  
  Example: `=IMCOS("1+1i")` → `0.833730025-0.988897706i`
- **IMEXP**: Returns the exponential of a complex number.  
  Example: `=IMEXP("1+1i")` → `1.468693939+2.287355287i`
- **IMLOG**: Returns the natural logarithm of a complex number.  
  Example: `=IMLOG("1+1i")` → `0.346573591+0.785398163i`

### Summary:

The `IMTAN` function in Excel provides a simple and efficient way to find the tangent of complex numbers, making it an
essential tool for numerical computations involving trigonometric operations in both real and imaginary domains.