<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMSECH Function

The `IMSECH` function in Excel calculates the hyperbolic secant of a given complex number. This function is primarily
used in mathematical, engineering, and scientific contexts involving complex numbers and hyperbolic trigonometric
computations.

### Key Features of IMSECH:

- Computes the hyperbolic secant of a complex number in the form `a+bi` or `a+bj`.
- Works with both real and complex numbers.
- Returns the result as a complex number, even if the imaginary part is `0`.

### Syntax:

```plaintext
IMSECH(inumber)
```

- **inumber**: The complex number whose hyperbolic secant needs to be calculated. This can be:
    - A string, such as `"5+3i"`.
    - A cell reference containing a valid complex number.
    - A real number (treated as a complex number with an imaginary part of `0`).

### Formula Details:

The hyperbolic secant of a complex number is defined as:

```plaintext
sech(z) = 1 / cosh(z)
```

Where `z` is the complex number input, and `cosh(z)` is its hyperbolic cosine.

### Examples:

1. **Calculating the Hyperbolic Secant of a Complex Number**:  
   `=IMSECH("4+2i")`  
   The hyperbolic secant of `4+2i` is:  
   **Result**: `-0.0362534969 - 0.0051643446i`

2. **Calculating Hyperbolic Secant with a Real Input**:  
   `=IMSECH(3)`  
   For real numbers, the hyperbolic secant is computed as `1/cosh(real part)`:  
   **Result**: `0.0993279274`

3. **Handling a Purely Imaginary Number**:  
   `=IMSECH("0+3i")`  
   The hyperbolic secant of `3i` is:  
   **Result**: `0.9950547537 - 0.9950547537i`

4. **Using a Cell Reference**:  
   If cell `A1` contains `"3-4i"`, then:  
   `=IMSECH(A1)`  
   The hyperbolic secant of `3-4i` is:  
   **Result**: `-0.0417572559 - 0.0681247048i`

5. **Complex Value From Formula**:  
   `=IMSECH(COMPLEX(1, -1))`  
   If you create the complex number `1-i` using the `COMPLEX` function, the hyperbolic secant of this value is:  
   **Result**: `1.8508157177 - 0.313201924i`

6. **Inputting Zero**:  
   `=IMSECH(0)`  
   Since the hyperbolic secant of `0` is `1/cosh(0)` and `cosh(0)` is `1`:  
   **Result**: `1`

### Notes:

- If the input (**inumber**) is not formatted as a valid complex number, Excel will return a `#VALUE!` error.
- The function uses radians for hyperbolic calculations. Use the `RADIANS` function to convert degrees to radians if
  needed.
- Output will always be expressed as a complex number.

# IMSECH - Precision Differences Between Excel and Codcel

## Function

`IMSECH` returns the hyperbolic secant of a complex number, defined as `1 / cosh(z)`.

## Observed Difference

When computing `IMSECH` for certain complex inputs, the Codcel Rust implementation may produce a result with a different **15th significant digit** compared to Excel. In some cases, Excel's result appears to have one fewer significant digit because its 15th digit is a trailing zero that gets stripped.

### Example

| Input | Excel Result | Codcel Result |
|-------|-------------|---------------|
| `3+4i` | `-0.065294027857947+0.0752249603027732i` | `-0.0652940278579471+0.0752249603027732i` |

The real component shows: Excel `...57947` (14 visible digits, effectively `...579470` with trailing zero stripped) vs Codcel `...579471` (15 digits). The difference is in the 15th significant digit.

## Why This Happens

`IMSECH(a+bi)` is computed as `1 / cosh(a+bi)`, which involves:

```
cosh(a+bi) = cosh(a)*cos(b) + i*sinh(a)*sin(b)
sech(a+bi) = 1 / cosh(a+bi)
```

This requires calls to `cosh`, `sinh`, `cos`, `sin` and then a complex division. Each of these operations can round differently at the bit level across platforms:

- **Excel** uses the Windows MSVC runtime math library.
- **Codcel** uses Rust's standard library / platform C math library.

In this case, the cascade of rounding differences results in the 15th significant digit differing. Excel computes `...579470` (which displays as `...57947` after trailing zero removal), while Codcel computes `...579471`.

## Why It Looks Like Fewer Digits

Both Excel and Codcel format numbers with up to 15 significant digits and strip trailing zeros. When the 15th digit happens to be `0`, it gets removed, making the displayed result appear shorter. This is purely a display difference - both systems are working with 15-digit precision internally.

## Impact

- The difference is at the level of **1 part in 10^15** (one quadrillionth).
- This is within the precision limit of IEEE 754 double-precision floating-point (~15.9 significant decimal digits).
- No practical calculation would be affected by this difference.

## What You Can Do

- If comparing results between Excel and Codcel, use a tolerance of at least `1e-14` for each component rather than exact string equality.
- When parsing complex number strings for comparison, convert components to floating-point values and compare numerically rather than comparing strings.


### Applications:

- **Engineering**: Useful in fields such as electronics and control systems involving hyperbolic functions.
- **Mathematics**: Essential for evaluating equations involving hyperbolic trigonometric relationships.
- **Data Analysis**: Supports extensions of periodic behavior modeling using complex hyperbolic functions.

### Related Functions:

- **IMCOSH**: Returns the hyperbolic cosine of a complex number.  
  Example: `=IMCOSH("3+4i")` → `-6.5806630401 - 7.5815527427i`
- **IMSINH**: Returns the hyperbolic sine of a complex number.  
  Example: `=IMSINH("3+4i")` → `6.5481200409 - 7.6192317203i`
- **IMSEC**: Computes the secant of a complex number.  
  Example: `=IMSEC("3+4i")` → `-0.0652940279 + 0.0752206537i`
- **IMCOTH**: Returns the hyperbolic cotangent of a complex number.
  Example: `=IMCOTH("2+i")` → `0.3799489623 - 0.2298488471i`

### Summary:

The `IMSECH` function in Excel is a powerful tool for performing hyperbolic trigonometric operations on complex numbers.
Its use cases include advanced mathematical modeling, engineering solutions, and systems analysis involving hyperbolic
computations.