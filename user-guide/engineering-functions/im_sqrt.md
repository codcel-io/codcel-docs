<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMSQRT Function

The `IMSQRT` function in Excel calculates the square root of a given complex number. This function is particularly
useful in mathematical, engineering, and scientific contexts that involve complex number computations.

### Key Features of IMSQRT:

- Computes the square root of a complex number expressed in the form `a+bi` or `a+bj`.
- Works with both real and complex numbers.
- Returns the result as a complex number, even if the imaginary part is `0`.

### Syntax:

```plaintext
IMSQRT(inumber)
```

- **inumber**: The complex number for which the square root is to be calculated. This can be:
    - A string, such as `"5+3i"`.
    - A cell reference containing a valid complex number.
    - A real number (interpreted as a complex number with an imaginary part of `0`).

### Formula Details:

The square root of a complex number `z`, where `z = x + yi` (with `x` as the real part and `y` as the imaginary part),
is defined as:

```plaintext
sqrt(z) = ±(sqrt(r) * cos(θ/2) + i * sqrt(r) * sin(θ/2))
```

Where:

- `r` is the magnitude (absolute value) of the complex number, calculated as `sqrt(x^2 + y^2)`.
- `θ` is the argument (angle) of the complex number in polar coordinates, calculated as `atan2(y, x)`.

Excel simplifies these steps and directly outputs the square root as a complex number.

### Examples:

1. **Calculating the Square Root of a Complex Number**:  
   `=IMSQRT("4+9i")`  
   For `4 + 9i`, the square root is:  
   **Result**: `2.581988897 + 1.742396482i`

2. **Calculating Square Root with a Real Input**:  
   `=IMSQRT(16)`  
   For real numbers, the square root is a real number:  
   **Result**: `4`

3. **Handling Purely Imaginary Numbers**:  
   `=IMSQRT("0-9i")`  
   For a purely imaginary input, the square root is:  
   **Result**: `2.121320344 - 2.121320344i`

4. **Using a Cell Reference**:  
   If cell `A1` contains `"6-8i"`, then:  
   `=IMSQRT(A1)`  
   The square root of `6 - 8i` is:  
   **Result**: `2.872281323 - 1.393070434i`

5. **Complex Value From Formula**:  
   `=IMSQRT(COMPLEX(3, -4))`  
   Using the `COMPLEX` function to generate `3 - 4i`, the square root is:  
   **Result**: `2 + i`

6. **Inputting Zero**:  
   `=IMSQRT(0)`  
   The square root of `0` is simply:  
   **Result**: `0`

### Notes:

- If the input (**inumber**) is not formatted as a valid complex number, Excel will return a `#VALUE!` error.
- The function returns both positive and negative roots, but typically resolves to the principal value.
- Output is always expressed as a complex number, even when the imaginary component is `0`.

# IMSQRT - Precision Differences Between Excel and Codcel

## Function

`IMSQRT` returns the square root of a complex number.

## Observed Difference

When computing `IMSQRT` of negative real numbers, the Codcel Rust implementation produces slightly different **floating-point noise** than Excel. The mathematically-zero real component shows a tiny non-zero residual, and the exact value of that residual differs between platforms.

### Examples

**IMSQRT(-1) (should mathematically equal i)**

| Platform | Result |
|----------|--------|
| Excel | `6.1257422745431E-17+i` |
| Codcel | `6.12323399573677E-17+i` |

**IMSQRT(-4) (should mathematically equal 2i)**

| Platform | Result |
|----------|--------|
| Excel | `1.22514845490862E-16+2i` |
| Codcel | `1.22464679914735E-16+2i` |

In both cases the real component (which should be exactly zero) shows a tiny residual that differs between platforms.

## Why This Happens

`IMSQRT` uses the polar form to compute the square root:

```
sqrt(z) = sqrt(r) * (cos(theta/2) + i*sin(theta/2))
```

For `sqrt(-1)`:

```
r = 1, theta = pi
sqrt(-1) = cos(pi/2) + i*sin(pi/2)
```

Mathematically, `cos(pi/2) = 0` and `sin(pi/2) = 1`. But in floating-point arithmetic, `cos(pi/2)` is not exactly zero because `pi` itself cannot be represented exactly in IEEE 754. The tiny residual depends on the platform's `cos` implementation:

- **Excel (Windows MSVC)**: `cos(pi/2) = 6.1257422745431E-17`
- **Rust (macOS/Linux libm)**: `cos(pi/2) = 6.12323399573677E-17`

Both are correct to within 1 ULP (unit in the last place) of the true mathematical result, but they differ due to different internal polynomial approximations used by each platform's math library.

For `sqrt(-4)`, the residual is `2 * cos(pi/2)`, so the same platform difference is scaled by 2.

## Why Not Just Zero It Out?

Excel itself preserves this floating-point noise rather than rounding it to zero. Codcel follows the same behavior, showing the actual computed result. This is the mathematically honest approach - both platforms are showing the real output of their floating-point computation.

## Impact

- The noise values are on the order of **10^-16 to 10^-17**, which is effectively zero.
- The mathematically-significant components (`i` and `2i`) match exactly.
- No real-world calculation would be affected. The noise is 16+ orders of magnitude smaller than the meaningful result.
- `sqrt(-1) = 6.12e-17 + i` is functionally identical to `sqrt(-1) = i`.

## What You Can Do

- If comparing results between Excel and Codcel, treat components smaller than `1e-14` relative to the largest component as effectively zero.
- If your application needs to detect purely imaginary results, use a threshold like `abs(real_part) < 1e-10 * abs(imag_part)` rather than checking for exact zero.
- When comparing formatted complex number strings numerically, parse the components as floats and compare with a tolerance (e.g., `1e-14`) rather than using exact string comparison.

## Technical Background

The root cause is that IEEE 754 cannot represent `pi` exactly. The closest double-precision value to `pi` is:

```
3.141592653589793115997963...
```

which differs from true `pi` by about `1.22e-16`. This means `cos(pi_float / 2)` computes the cosine of a value slightly different from `pi/2`, producing a tiny non-zero result. Different math libraries use different algorithms to compute `cos`, leading to slightly different (but equally valid) tiny residuals.


### Applications:

- **Engineering**: Useful for analyzing systems involving impedance, resonance, or waveforms.
- **Mathematics**: Provides the square root of complex numbers in advanced algebraic expressions.
- **Data Analysis**: Facilitates computations within datasets that involve complex numerical formulations.

### Related Functions:

- **IMSUM**: Adds two or more complex numbers.  
  Example: `=IMSUM("3+2i", "4-5i")` → `7 - 3i`
- **IMSUB**: Subtracts two complex numbers.  
  Example: `=IMSUB("8+3i", "5+4i")` → `3 - i`
- **IMMULT**: Multiplies two complex numbers.  
  Example: `=IMMULT("1+2i", "3-4i")` → `11 + 2i`
- **IMDIV**: Divides one complex number by another.  
  Example: `=IMDIV("7+6i", "4+3i")` → `2 - i`

### Summary:

The `IMSQRT` function in Excel is an essential tool for calculating the square root of complex numbers. Its versatility
makes it a valuable function for those working in engineering, mathematics, and scientific computational fields.