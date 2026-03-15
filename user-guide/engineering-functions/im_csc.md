<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMCSC Function

The `IMCSC` function in Excel calculates the **cosecant** of a given complex number. It is designed to handle complex
numbers represented in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary part.

This function is particularly useful in advanced mathematical and engineering applications, especially when working with
trigonometric operations involving complex numbers.

### Key Features of IMCSC:

- Computes the **cosecant** of a complex number.
- Accepts inputs as text strings (e.g., `"a+bi"`), cell references containing complex numbers, or results from other
  functions like `COMPLEX`.
- Returns a complex number as the result.

### Syntax:

```plaintext
IMCSC(inumber)
```

- **inumber**: The complex number for which you want to compute the cosecant. This can be provided as:
    - A text string such as `"2+3i"`.
    - A reference to a cell containing a valid complex number.
    - The output from the `COMPLEX` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the cosecant is calculated using the formula:

```plaintext
csc(z) = 1 / sin(z)
```

Where:

- **sin(z)** is the trigonometric sine of the complex number `z`.
- **a** is the real part of `z`.
- **b** is the imaginary part of `z`.

### Examples:

1. **Cosecant of a Complex Number**:  
   `=IMCSC("1+2i")`  
   For the complex number `1+2i`, the returned value is:  
   **Result**: ~`-0.03272208722 - 0.09332054532i`

2. **Using a Reference to a Complex Number**:  
   If cell `A1` contains `"3-4i"`, then:  
   `=IMCSC(A1)`  
   Returns the cosecant of `3-4i`:  
   **Result**: ~`-0.05552752069 + 0.02784177812i`

3. **Cosecant of a Purely Real Number**:  
   `=IMCSC("3")`  
   For purely real numbers, the result is the standard cosecant:  
   **Result**: ~`7.08616739574`

4. **Cosecant of a Purely Imaginary Number**:  
   `=IMCSC("0+2i")`  
   For purely imaginary numbers, the result is:  
   **Result**: ~`0 + 0.27572056477i`

### Notes:

- If **inumber** is not a valid complex number, the function will return a `#NUM!` error.
- Complex numbers in Excel can be created using the `COMPLEX(real_num, imaginary_num)` function. For example:  
  `=COMPLEX(5, -3)` generates the complex number `5-3i`.
- The trigonometric cosecant is undefined for cases where `sin(z) = 0`. If this occurs, the function returns a
  `#DIV/0!` error.

# IMCSC - Precision Differences Between Excel and Codcel

## Function

`IMCSC` returns the cosecant of a complex number, defined as `1 / sin(z)`.

## Observed Difference

When computing `IMCSC` for certain complex inputs, the Codcel Rust implementation may differ from Excel in the **last (15th) significant digit** of one or both components.

### Example

| Input | Excel Result | Codcel Result |
|-------|-------------|---------------|
| `1-2i` | `0.621518017170428-0.303931001628427i` | `0.621518017170429-0.303931001628426i` |

Both the real and imaginary components differ by 1 in the 15th significant digit.

## Why This Happens

`IMCSC(a+bi)` is computed as `1 / IMSIN(a+bi)`, which expands to:

```
sin(a+bi) = sin(a)*cosh(b) + i*cos(a)*sinh(b)
csc(a+bi) = 1 / sin(a+bi)
```

The computation involves:
1. Calls to `sin`, `cos`, `cosh`, and `sinh` - each of which may round differently across platforms.
2. A complex division (`1 / z`), which further amplifies any last-bit differences.

Excel and Codcel use different underlying math libraries:

- **Excel** uses the Windows MSVC runtime math library.
- **Codcel** uses Rust's standard library / platform C math library.

Both are correct to within 1 ULP (unit in the last place), but their rounding choices can differ at the bit level. After multiple operations, this can result in the 15th significant digit differing by 1.

## Impact

- The difference is at the level of **1 part in 10^15** (one quadrillionth).
- This is well within the precision limit of IEEE 754 double-precision floating-point (~15.9 significant decimal digits).
- No practical calculation would be affected by this difference.

## What You Can Do

- If comparing results between Excel and Codcel, use a tolerance of at least `1e-14` for each component rather than exact string equality.
- If exact string matching with Excel is required, be aware that platform-level math library differences make this impossible to guarantee for trigonometric and hyperbolic function results.


### Applications:

- **Mathematics**: Extends trigonometric cosecant calculations into the complex plane.
- **Engineering**: Useful in the analysis of waveforms or oscillatory systems involving complex arguments.
- **Physics**: Critical when working with complex wave representations or phase relations.

### Related Functions:

- **IMSIN**: Returns the trigonometric sine of a complex number.  
  Example: `=IMSIN("2+3i")` → ~`9.15449914662 + 4.16890695997i`
- **IMCOT**: Returns the trigonometric cotangent of a complex number.  
  Example: `=IMCOT("2+3i")` → ~`0.03381282608 - 1.01479361614i`
- **IMSEC**: Returns the trigonometric secant of a complex number.  
  Example: `=IMSEC("2+3i")` → ~`-0.04167496441 + 0.09047320975i`

### Summary:

The `IMCSC` function enhances Excel’s capability for trigonometric computations in the complex domain. It is
particularly valuable for those working in advanced fields such as engineering, physics, and applied mathematics,
enabling the study and manipulation of cosecant functions in both real and complex planes.