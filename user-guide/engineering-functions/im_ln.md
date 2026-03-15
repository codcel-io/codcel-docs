<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMLN Function

The `IMLN` function in Excel calculates the natural logarithm of a complex number. This function is particularly useful
in mathematical, engineering, and scientific applications where logarithmic transformations in the complex domain are
required.

### Key Features of IMLN:

- Calculates the natural logarithm (`ln`) of complex numbers.
- Accepts complex numbers in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary part.
- Returns the result as a complex number in the same format: `c+di`.

### Syntax:

```plaintext
IMLN(inumber)
```

- **inumber**: The complex number for which you want to calculate the natural logarithm. This can be:
    - A text string such as `"3+4i"`.
    - A reference to a cell containing a valid complex number.
    - Created using the `COMPLEX(real_num, imaginary_num)` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the natural logarithm is calculated as:

```plaintext
ln(a+bi) = ln(|z|) + i * θ
```

Where:

- **|z|** is the magnitude of the complex number, i.e., `|z| = √(a² + b²)`.
- **θ** is the phase angle of the complex number, i.e., `θ = atan(b/a)` (the arctangent of `b/a`).
- The result is expressed in the form of `c+di`, where:
    - **c = ln(|z|)** is the natural logarithm of the magnitude.
    - **d = θ** is the phase angle in radians.

### Examples:

1. **Natural Logarithm of a Complex Number**:  
   `=IMLN("1+2i")`  
   For the complex number `1+2i`, the result is:  
   **Result**: ~`0.804718956 + 1.107148718i`

2. **Logarithm of a Purely Real Positive Number**:  
   `=IMLN(5)`  
   For the real number `5`, the result is:  
   **Result**: `1.609437912` (since `ln(5) ≈ 1.609` and the phase angle is `0`)

3. **Logarithm of a Purely Real Negative Number**:  
   `=IMLN(-1)`  
   For the real number `-1`, the result is:  
   **Result**: `0 + πi` (since the phase angle for `-1` is `π` radians)

4. **Logarithm of Zero**:  
   `=IMLN(0)`  
   **Result**: Produces an error (`#NUM!`) because the logarithm of zero is undefined.

5. **Using a Reference for a Complex Input**:  
   If cell `A1` contains `"2-3i"`, then:  
   `=IMLN(A1)`  
   **Result**: ~`1.282474678 - 0.982793723i`

### Notes:

- The `IMLN` function handles both real and imaginary components. When the input is a purely real number, the result
  simplifies accordingly.
- If **inumber** is invalid or not recognized as a complex number, Excel will return a `#VALUE!` error.
- Use the `COMPLEX` function to create a valid complex number for input. For example:  
  `=COMPLEX(3, 4)` provides the equivalent of `3+4i`.

### Applications:

- **Mathematics**: Solves equations involving natural logarithms of complex numbers.
- **Engineering**: Analyzes phase differences in alternating current (AC) circuits.
- **Physics**: Handles complex wavefunctions and logarithmic transformations in quantum mechanics.
- **Data Science**: Supports transformations in domains involving complex-valued signals.

### Related Functions:

- **IMEXP**: Computes the exponential of a complex number.  
  Example: `=IMEXP("0.804718956+1.107148718i")` → `1+2i`
- **IMLOG10**: Calculates the base-10 logarithm of a complex number.  
  Example: `=IMLOG10("3+4i")` → `0.69897 + 0.93343i`
- **IMLOG2**: Calculates the base-2 logarithm of a complex number.  
  Example: `=IMLOG2("3+4i")` → `1.01064 + 1.34839i`
- **IMPOWER**: Raises a complex number to a given power.  
  Example: `=IMPOWER("2+3i", 3)` → `-46+9i`

### Summary:

The `IMLN` function is a fundamental tool for working with complex numbers in Excel, making it highly valuable for
advanced computations in mathematics, engineering, and science. Its ability to provide logarithmic transformations with
both real and imaginary components allows for precise modeling of complex systems in various domains.