<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMSINH Function

The `IMSINH` function in Excel calculates the hyperbolic sine of a given complex number. This function is particularly
useful in mathematical, engineering, and scientific contexts involving hyperbolic functions with complex numbers.

### Key Features of IMSINH:

- Computes the hyperbolic sine of a complex number expressed in the form `a+bi` or `a+bj`.
- Works with both real and complex numbers.
- Returns the result as a complex number, even if the imaginary part is `0`.

### Syntax:

```plaintext
IMSINH(inumber)
```

- **inumber**: The complex number whose hyperbolic sine needs to be calculated. This can be:
    - A string, such as `"5+3i"`.
    - A cell reference containing a valid complex number.
    - A real number (interpreted as a complex number with an imaginary part of `0`).

### Formula Details:

The hyperbolic sine of a complex number `z`, where `z = x + yi` (with `x` as the real part and `y` as the imaginary
part), is defined as:

```plaintext
sinh(z) = sinh(x) * cos(y) + i * cosh(x) * sin(y)
```

Where:

- `sinh` and `cosh` are the hyperbolic sine and cosine of the real part (`x`).
- `sin` and `cos` are the standard trigonometric sine and cosine functions of the imaginary part (`y`).

### Examples:

1. **Calculating the Hyperbolic Sine of a Complex Number**:  
   `=IMSINH("2+3i")`  
   For `2 + 3i`, the hyperbolic sine is:  
   **Result**: `-3.59056459 + 0.53092109i`

2. **Calculating Hyperbolic Sine with a Real Input**:  
   `=IMSINH(3)`  
   For real numbers, the hyperbolic sine simplifies to the standard hyperbolic sine:  
   **Result**: `10.01787493`

3. **Handling Purely Imaginary Numbers**:  
   `=IMSINH("0+1i")`  
   For a purely imaginary input, `sinh(0 + yi)` simplifies to `i * sin(y)`:  
   **Result**: `0.84147098i`

4. **Using a Cell Reference**:  
   If cell `A1` contains `"4-2i"`, then:  
   `=IMSINH(A1)`  
   The hyperbolic sine of `4 - 2i` is:  
   **Result**: `-27.01681326 + 3.85115334i`

5. **Complex Value From Formula**:  
   `=IMSINH(COMPLEX(-1, 2))`  
   Using the `COMPLEX` function to generate `-1 + 2i`, the hyperbolic sine is:  
   **Result**: `-1.95960104 + 3.16577851i`

6. **Inputting Zero**:  
   `=IMSINH(0)`  
   The hyperbolic sine of `0` is simply:  
   **Result**: `0`

### Notes:

- If the input (**inumber**) is not formatted as a valid complex number, Excel will return a `#VALUE!` error.
- The function uses radians for trigonometric and hyperbolic calculations. Convert degrees to radians using the
  `RADIANS` function if necessary.
- Output is always expressed as a complex number, even when the imaginary component is `0`.

### Applications:

- **Engineering**: Useful for modeling systems that incorporate hyperbolic behavior, such as oscillations and waveforms.
- **Mathematics**: Helps solve equations and expressions involving the hyperbolic sine of complex numbers.
- **Data Analysis**: Facilitates advanced computations in scenarios requiring hyperbolic functions of real and imaginary
  components.

### Related Functions:

- **IMCOSH**: Returns the hyperbolic cosine of a complex number.  
  Example: `=IMCOSH("2+3i")` → `-3.72454550 - 0.51182257i`
- **IMSIN**: Calculates the sine of a complex number.  
  Example: `=IMSIN("4+3i")` → `-7.61923172 - 6.54812004i`
- **IMCOS**: Computes the cosine of a complex number.  
  Example: `=IMCOS("1+2i")` → `2.03272301 - 3.051897799i`
- **IMEXP**: Returns the exponential of a complex number.  
  Example: `=IMEXP("1+3i")` → `-2.691997 + 1.570796i`

### Summary:

The `IMSINH` function in Excel is a powerful tool for computing the hyperbolic sine of complex numbers. It is widely
used in engineering, mathematical research, and scientific computations that involve hyperbolic functions with complex
arguments.