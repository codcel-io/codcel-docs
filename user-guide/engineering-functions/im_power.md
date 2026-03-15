<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMPOWER Function

The `IMPOWER` function in Excel raises a complex number to a given power. This function is particularly useful in
mathematical, engineering, and scientific applications that involve complex number manipulation, such as solving
equations or analyzing electrical circuits.

### Key Features of IMPOWER:

- Computes the result of raising a complex number to a specified power.
- Accepts complex numbers in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary part.
- Returns the result as a complex number in the same format: `c+di`.

### Syntax:

```plaintext
IMPOWER(inumber, number)
```

- **inumber**: The complex number to be raised to the power. This input can be:
    - A text string such as `"3+2i"`.
    - A reference to a cell containing a valid complex number.
    - Created with the `COMPLEX(real_num, imaginary_num)` function.

- **number**: The exponent to which the complex number is raised. This can be a real number or a reference to a cell
  containing the number.

### Formula and Calculation:

For a complex number `z = a+bi` and a power `n`, the result is calculated as:

```plaintext
(a+bi)^n = |z|^n * (cos(nθ) + i * sin(nθ))
```

Where:

- **|z|**: The magnitude (absolute value) of the complex number, `|z| = √(a² + b²)`.
- **θ**: The phase angle of the complex number, `θ = atan(b/a)` (arctangent of `b/a`).
- The result is expressed in polar form and converted back to rectangular form as `c+di`.

### Examples:

1. **Cube of a Complex Number**:  
   `=IMPOWER("1+2i", 3)`  
   For the complex number `1+2i` raised to the power of 3, the result is:  
   **Result**: `-11+2i`

2. **Square of a Complex Number**:  
   `=IMPOWER("3+4i", 2)`  
   For `3+4i`, the result is:  
   **Result**: `-7+24i`

3. **Raising a Real Number to a Power**:  
   `=IMPOWER(5, 2)`  
   For the real number `5` squared, the result is:  
   **Result**: `25` (since there is no imaginary part).

4. **Complex Number Raised to Zero**:  
   `=IMPOWER("1+1i", 0)`  
   Any number raised to the power of 0 results in:  
   **Result**: `1` (independent of the number's real and imaginary parts).

5. **Using a Reference for Input**:  
   If cell `A1` contains `"2-3i"` and cell `A2` contains `4`, then:  
   `=IMPOWER(A1, A2)`  
   **Result**: `-119-120i`

### Notes:

- If **inumber** is not a valid complex number or the format is incorrect, Excel returns a `#VALUE!` error.
- Negative or fractional powers of complex numbers are supported by `IMPOWER`. The function handles these cases using
  logarithms and polar coordinates.

# IMPOWER - Precision Differences Between Excel and Codcel

## Function

`IMPOWER` raises a complex number to a given power.

## Observed Difference

When computing `IMPOWER` for purely imaginary bases, the Codcel Rust implementation produces slightly different **floating-point noise** than Excel. The mathematically-zero component shows a tiny non-zero residual, and the exact value of that residual differs between platforms.

### Examples

**i^4 (should mathematically equal 1)**

| Platform | Result |
|----------|--------|
| Excel | `1-2.45029690981724E-16i` |
| Codcel | `1-2.44929359829471E-16i` |

**(2i)^3 (should mathematically equal -8i)**

| Platform | Result |
|----------|--------|
| Excel | `-1.47017814589034E-15-8i` |
| Codcel | `-1.46957615897483E-15-8i` |

In both cases the "noise" component (the one that should be exactly zero) differs slightly.

## Why This Happens

`IMPOWER` uses the polar form to compute complex powers:

```
z^n = r^n * (cos(n*theta) + i*sin(n*theta))
```

For `i^4`, the computation becomes:

```
r = 1, theta = pi/2
z^4 = cos(2*pi) + i*sin(2*pi)
```

Mathematically, `sin(2*pi) = 0` and `cos(2*pi) = 1`. But in floating-point arithmetic, `sin(2*pi)` is not exactly zero - it produces a tiny residual on the order of 10^-16. The exact value of this residual depends on the platform's implementation of `sin`:

- **Excel (Windows MSVC)**: `sin(2*pi) = -2.45029690981724E-16`
- **Rust (macOS/Linux libm)**: `sin(2*pi) = -2.44929359829471E-16`

Both values are correct to within 1 ULP of the true result (zero), but they differ because `sin` and `cos` are implemented using different polynomial approximations on each platform.

The same principle applies to `(2i)^3`, where `cos(3*pi/2)` produces a tiny non-zero residual that differs between platforms.

## Why Not Just Zero It Out?

Excel itself preserves this floating-point noise rather than rounding it to zero. Codcel follows the same behavior - showing the actual computed result rather than applying a cleanup threshold. This ensures transparency: what you see is exactly what the floating-point computation produced.

## Impact

- The "noise" values are on the order of **10^-15 to 10^-16**, which is effectively zero.
- The mathematically-significant components (`1` for i^4, `-8i` for (2i)^3) match exactly.
- No real-world calculation would be affected, as these noise values are 15+ orders of magnitude smaller than the meaningful result.

## What You Can Do

- If comparing results between Excel and Codcel, treat components smaller than `1e-14` relative to the largest component as effectively zero.
- Alternatively, compare floating-point values with a tolerance rather than comparing formatted strings.
- If your application requires detecting when a result is "purely real" or "purely imaginary", use a threshold like `abs(component) < 1e-10 * abs(other_component)` rather than checking for exact zero.


### Applications:

- **Engineering**: Used in electrical and control systems for signal analysis and feedback design.
- **Mathematics**: Solves polynomial equations and complex transformations.
- **Physics**: Analyzes waveforms and resonance involving complex impedance.
- **Data Science**: Supports transformations of multi-dimensional datasets.

### Related Functions:

- **IMPRODUCT**: Multiplies two or more complex numbers.  
  Example: `=IMPRODUCT("2+3i", "4-5i")` → `23+2i`
- **IMDIV**: Divides one complex number by another.  
  Example: `=IMDIV("3+4i", "1+2i")` → `2-1i`
- **IMSUM**: Adds two or more complex numbers.  
  Example: `=IMSUM("2+3i", "1-2i")` → `3+1i`
- **IMABS**: Returns the magnitude (absolute value) of a complex number.  
  Example: `=IMABS("3+4i")` → `5`

### Summary:

The `IMPOWER` function enables users to perform complex number power calculations efficiently in Excel. It is a critical
tool for mathematical computations, signal processing, and other applications requiring complex arithmetic. Its ability
to handle both real and imaginary components ensures robust functionality across various disciplines.