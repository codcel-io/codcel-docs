<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMCOSH Function

The `IMCOSH` function in Excel returns the **hyperbolic cosine** of a given complex number. It is specifically designed
to handle calculations involving complex numbers in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the
imaginary part.

This function is particularly useful in advanced mathematical and engineering applications, especially when working with
hyperbolic trigonometric operations in the domain of complex numbers.

### Key Features of IMCOSH:

- Computes the **hyperbolic cosine** of a complex number.
- Accepts inputs as text strings (`"a+bi"`), cell references containing complex numbers, or results from functions like
  `COMPLEX`.
- Returns a complex number as the result.

### Syntax:

```plaintext
IMCOSH(inumber)
```

- **inumber**: The complex number for which you want to compute the hyperbolic cosine. This can be provided as:
    - A text string like `"2+3i"`.
    - A reference to a cell containing a valid complex number.
    - The output from the `COMPLEX` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the hyperbolic cosine is calculated using the formula:

```plaintext
cosh(z) = cosh(a) * cos(b) + i * sinh(a) * sin(b)
```

Where:

- **a** is the real part of `z`.
- **b** is the imaginary part of `z`.
- `cosh`, `sinh` are hyperbolic functions.
- `cos`, `sin` are standard trigonometric functions.

### Examples:

1. **Hyperbolic Cosine of a Complex Number**:  
   `=IMCOSH("1+2i")`  
   For the complex number `1+2i`, the returned value is:  
   **Result**: ~`5.03269379344 - 3.05189779915i`

2. **Use a Reference to a Complex Number**:  
   If cell `A1` contains `"0-3i"`, then:  
   `=IMCOSH(A1)`  
   Returns the hyperbolic cosine of `0-3i`:  
   **Result**: ~`-10.06766199578`

3. **Hyperbolic Cosine of a Purely Real Number**:  
   `=IMCOSH("3")`  
   For purely real numbers, the result is the standard hyperbolic cosine:  
   **Result**: ~`10.06766199578`

4. **Hyperbolic Cosine of a Purely Imaginary Number**:  
   `=IMCOSH("0+2i")`  
   For purely imaginary numbers, the result involves trigonometric functions:  
   **Result**: ~`-1.56732437063 + 0.00000000000i`

### Notes:

- If **inumber** is not a valid complex number, the function will return a `#NUM!` error.
- Complex numbers in Excel can be created using the `COMPLEX(real_num, imaginary_num)` function. For example:  
  `=COMPLEX(4, -5)` generates the complex number `4-5i`.

# IMCOSH - Precision Differences Between Excel and Codcel

## Function

`IMCOSH` returns the hyperbolic cosine of a complex number.

## Observed Difference

When computing `IMCOSH` for certain complex inputs, the Codcel Rust implementation may differ from Excel in the **last (15th) significant digit** of one or both components.

### Example

| Input | Excel Result | Codcel Result |
|-------|-------------|---------------|
| `3+4i` | `-6.58066304055116-7.58155274274654i` | `-6.58066304055116-7.58155274274655i` |

The imaginary component differs by 1 in the 15th significant digit: Excel produces `...4654`, Codcel produces `...4655`.

## Why This Happens

`IMCOSH(a+bi)` is computed as:

```
cosh(a+bi) = cosh(a)*cos(b) + i*sinh(a)*sin(b)
```

This involves calls to the underlying math library's `cosh`, `sinh`, `cos`, and `sin` functions. These transcendental functions are implemented differently across platforms:

- **Excel** uses the math library bundled with Windows (MSVC runtime).
- **Codcel** uses Rust's `libm` / the platform's C math library (e.g., macOS `libSystem`, Linux `glibc`).

Both implementations are correct to within 1 ULP (unit in the last place) of the true mathematical result, but they may round the final bit differently. When these tiny rounding differences propagate through multiplication and addition, the final result can differ by 1 in the 15th significant digit.

## Impact

- The difference is at the level of **1 part in 10^15** (one quadrillionth).
- This is well within the inherent precision limit of IEEE 754 double-precision floating-point arithmetic (~15.9 significant decimal digits).
- No real-world engineering or financial calculation would be affected by this difference.

## What You Can Do

- If your application compares complex number results between Excel and Codcel, use a tolerance of at least `1e-14` for the real and imaginary components rather than exact string equality.
- If you need exact string matching with Excel, be aware that platform-level math library differences make this impossible to guarantee for transcendental function results.

### Applications:

- **Mathematics**: Extends hyperbolic cosine operations into the complex plane, useful for advanced calculations.
- **Engineering**: Commonly used in signal processing, control systems, and other fields that model exponential growth
  or decay.
- **Physics**: Useful when working with hyperbolic functions in relativistic and wave mechanics.

### Related Functions:

- **IMSINH**: Returns the hyperbolic sine of a complex number.  
  Example: `=IMSINH("2+3i")` → ~`-3.59056458999 + 0.53092108625i`
- **IMCOS**: Returns the trigonometric cosine of a complex number.  
  Example: `=IMCOS("2+3i")` → ~`2.03272300702 - 3.05189779915i`
- **IMEXP**: Returns the exponential of a complex number.  
  Example: `=IMEXP("1+2i")` → ~`-1.13120438376 + 2.47172667200i`
- **IMARGUMENT**: Returns the argument (angle) of a complex number.  
  Example: `=IMARGUMENT("3+4i")` → ~`0.93 radians`

### Summary:

The `IMCOSH` function enriches the Excel toolkit by enabling hyperbolic trigonometric calculations in the complex number
domain. Whether solving mathematical equations, modeling exponential phenomena, or performing engineering computations,
the `IMCOSH` function is a versatile tool for complex number operations.