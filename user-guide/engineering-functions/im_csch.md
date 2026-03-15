<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMCHSCH Function

The `IMCHSCH` function in Excel calculates the **hyperbolic cosecant (csch)** of a given complex number. This function
is tailored for handling complex numbers, represented in the form `a+bi` or `a+bj`, where `a` is the real part and `b`
is the imaginary part.

This function is especially useful in advanced mathematical and engineering applications, particularly when working with
hyperbolic trigonometric operations in the complex domain.

### Key Features of IMCHSCH:

- Computes the **hyperbolic cosecant** of a complex number.
- Accepts inputs as text strings (e.g., `"a+bi"`), cell references containing complex numbers, or results from functions
  like `COMPLEX`.
- Returns a complex number as the result.

### Syntax:

```plaintext
IMCHSCH(inumber)
```

- **inumber**: The complex number for which you want to compute the hyperbolic cosecant. This can be:
    - A text string such as `"1+2i"`.
    - A reference to a cell containing a valid complex number.
    - Created using the `COMPLEX(real_num, imaginary_num)` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the hyperbolic cosecant is calculated using the formula:

```plaintext
csch(z) = 1 / sinh(z)
```

Where:

- **sinh(z)** is the hyperbolic sine of the complex number `z`.
- **a** is the real part of `z`.
- **b** is the imaginary part of `z`.

### Examples:

1. **Hyperbolic Cosecant of a Complex Number**:  
   `=IMCHSCH("2+3i")`  
   For the complex number `2+3i`, this returns:  
   **Result**: ~`0.09047320975 - 0.04120098629i`

2. **Using a Reference to a Complex Number**:  
   If cell `A1` contains `"1-2i"`, then:  
   `=IMCHSCH(A1)`  
   Hyperbolic cosecant of `1-2i`:  
   **Result**: ~`0.22150093085 - 0.63549379925i`

3. **Hyperbolic Cosecant of a Purely Real Number**:  
   `=IMCHSCH("2")`  
   For purely real numbers, the result is the standard hyperbolic cosecant:  
   **Result**: ~`0.27572056477`

4. **Hyperbolic Cosecant of a Purely Imaginary Number**:  
   `=IMCHSCH("0+2i")`  
   For purely imaginary numbers, this returns:  
   **Result**: ~`0 - 0.27572056477i`

### Notes:

- If **inumber** is not a valid complex number, the function will return a `#NUM!` error.
- Hyperbolic cosecant is undefined for cases where `sinh(z) = 0`. In such cases, Excel returns a `#DIV/0!` error.
- Complex numbers in Excel can be generated using the `COMPLEX(real_num, imaginary_num)` function. For example:  
  `=COMPLEX(3, 4)` creates the complex number `3+4i`.

### Applications:

- **Mathematics**: Extends hyperbolic trigonometric functions into the complex plane, aiding analysis and computations.
- **Engineering**: Assists in modeling and analyzing systems or waveforms involving hyperbolic functions with complex
  numbers.
- **Physics**: Useful in scenarios involving relativistic motion, wave equations, or quantum mechanics.

### Related Functions:

- **IMSINH**: Returns the hyperbolic sine of a complex number.  
  Example: `=IMSINH("2+3i")` → ~`-3.59056458999 + 0.53092108625i`
- **IMSECH**: Returns the hyperbolic secant of a complex number.  
  Example: `=IMSECH("2+3i")` → ~`-0.04167496441 - 0.09047320975i`
- **IMCOSH**: Returns the hyperbolic cosine of a complex number.  
  Example: `=IMCOSH("2+3i")` → ~`-3.72454550492 - 0.51182256999i`

### Summary:

The `IMCHSCH` function empowers Excel users to work with hyperbolic trigonometric calculations in the complex domain. It
is a valuable tool for professionals and researchers in fields like engineering, physics, and applied mathematics, where
accurate and efficient handling of hyperbolic cosecant functions is essential.