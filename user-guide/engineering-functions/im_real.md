<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMREAL Function

The `IMREAL` function in Excel extracts the real part of a given complex number. It is useful in mathematical,
engineering, and scientific applications where distinguishing between the real and imaginary components of a complex
number is required.

### Key Features of IMREAL:

- Extracts the real part of a complex number in the form `a+bi` or `a+bj`, where `a` represents the real part.
- Returns the real part as a numeric value.
- If the input is a real number (with an imaginary part of `0` or unspecified), the function returns the input as is.

### Syntax:

```plaintext
IMREAL(inumber)
```

- **inumber**: The complex number from which the real part is to be extracted. This can be:
    - A string, such as `"5+3i"`.
    - A cell reference containing a valid complex number.
    - A number (real numbers are valid inputs, treated as complex numbers with no imaginary part).

### Formula Details:

If the input complex number is in the form `a+bi`, the `IMREAL` function returns `a` (the real component).

### Examples:

1. **Extracting the Real Part from a Complex Number**:  
   `=IMREAL("4+5i")`  
   The real part of `4+5i` is:  
   **Result**: `4`

2. **Extracting the Real Part from a Purely Real Number**:  
   `=IMREAL(7)`  
   There is no imaginary part for `7`, so the function returns:  
   **Result**: `7`

3. **Handling Complex Numbers in Cells**:  
   If cell `A1` contains `"3-2i"`, then:  
   `=IMREAL(A1)`  
   The real part from `3-2i` is:  
   **Result**: `3`

4. **Using a Generated Complex Number**:  
   `=IMREAL(COMPLEX(5, -8))`  
   Here the `COMPLEX` function creates `5-8i`. The real part is:  
   **Result**: `5`

5. **Handling a Purely Imaginary Number**:  
   `=IMREAL("0+6i")`  
   A purely imaginary number like `6i` has no real component:  
   **Result**: `0`

6. **Handling Zero as Input**:  
   `=IMREAL(0)`  
   The function returns:  
   **Result**: `0`

### Notes:

- If the input (**inumber**) is not a valid complex number or incorrectly formatted, Excel will return a `#VALUE!`
  error.
- The function seamlessly handles both real numbers and valid complex numbers.

### Applications:

- **Engineering**: Allows separation of the real part of impedance in electrical circuit analysis.
- **Data Analysis**: Useful for manipulating datasets involving multidimensional or imaginary values.
- **Mathematics**: Assists in solving equations and transformations involving complex numbers.

### Related Functions:

- **IMAGINARY**: Returns the imaginary part of a complex number.  
  Example: `=IMAGINARY("5-3i")` → `-3`
- **IMCOMPLEX**: Creates a complex number from real and imaginary parts.  
  Example: `=COMPLEX(3, 4)` → `"3+4i"`
- **IMABS**: Returns the magnitude (absolute value) of a complex number.  
  Example: `=IMABS("3+4i")` → `5`
- **IMARGUMENT**: Returns the argument (angle) of a complex number in radians.  
  Example: `=IMARGUMENT("1+√3i")` → `1.047`

### Summary:

The `IMREAL` function in Excel is an essential tool for extracting the real part of a complex number. Whether working
with engineering data, performing mathematical transformations, or separating components of a signal, it provides
critical functionality for handling complex values effectively.