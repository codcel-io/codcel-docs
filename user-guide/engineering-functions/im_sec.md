<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMSEC Function

The `IMSEC` function in Excel calculates the secant of a given complex number. This function is used in mathematical,
engineering, and scientific contexts involving complex trigonometric computations.

### Key Features of IMSEC:

- Computes the secant of a complex number in the form `a+bi` or `a+bj`.
- Works seamlessly with both real and complex numbers.
- Returns the result as a complex number.

### Syntax:

```plaintext
IMSEC(inumber)
```

- **inumber**: The complex number whose secant needs to be calculated. This can be:
    - A string, such as `"5+3i"`.
    - A cell reference containing a valid complex number.
    - A real number (treated as a complex number with an imaginary part of `0`).

### Formula Details:

The secant of a complex number is defined as:

```plaintext
sec(z) = 1 / cos(z)
```

Where `z` is the input complex number, and `cos(z)` is its cosine.

### Examples:

1. **Calculating the Secant of a Complex Number**:  
   `=IMSEC("4+2i")`  
   The secant of `4+2i` is:  
   **Result**: `-0.0362534969 - 0.0051643446i`

2. **Calculating Secant with a Real Input**:  
   `=IMSEC(3)`  
   For real numbers, the secant is computed as `1/cos(real part)`:  
   **Result**: `-7.086167395`

3. **Handling a Purely Imaginary Number**:  
   `=IMSEC("0+3i")`  
   The secant of `3i` is:  
   **Result**: `0.9950547537 - 0.9950547537i`

4. **Using a Cell Reference**:  
   If cell `A1` contains `"3-4i"`, then:  
   `=IMSEC(A1)`  
   The secant of `3-4i` is:  
   **Result**: `-0.0652940279 + 0.0752206537i`

5. **Complex Value From Formula**:  
   `=IMSEC(COMPLEX(1, -1))`  
   If you create the complex number `1-i` using the `COMPLEX` function, the secant of this value is:  
   **Result**: `0.4983370306 + 0.5910838417i`

6. **Inputting Zero**:  
   `=IMSEC(0)`  
   Since the secant of `0` is `1/cos(0)` and `cos(0)` is `1`:  
   **Result**: `1`

### Notes:

- If the input (**inumber**) is invalid or not properly formatted as a complex number, Excel will return a `#VALUE!`
  error.
- The function uses radians for trigonometric calculations. Use the `RADIANS` function if you need to convert degrees to
  radians.
- The result is returned in the form of a complex number, even if the imaginary part is `0`.

### Applications:

- **Engineering**: Useful in signal processing and control systems involving trigonometric transforms.
- **Data Analysis**: Allows modeling and analysis of systems with oscillatory or periodic behavior.
- **Mathematics**: Essential for solving equations and transformations involving complex trigonometric functions.

### Related Functions:

- **IMCOS**: Returns the cosine of a complex number.  
  Example: `=IMCOS("3+4i")` → `-27.0349456 - 3.8511533345i`
- **IMSIN**: Returns the sine of a complex number.  
  Example: `=IMSIN("3+4i")` → `3.8537380379 - 27.016813258i`
- **IMCOSH**: Returns the hyperbolic cosine of a complex number.  
  Example: `=IMCOSH("3+4i")` → `-6.5806630401 - 7.5815527427i`
- **IMSECH**: Calculates the hyperbolic secant of a complex number.  
  Example: `=IMSECH("3+i")` → `-0.0416749646 - 0.0906111372i`

### Summary:

The `IMSEC` function in Excel provides a crucial mechanism for calculating the secant of complex numbers. This
functionality is indispensable for applications in engineering, mathematics, and data analysis where precise handling of
complex trigonometric relationships is required.