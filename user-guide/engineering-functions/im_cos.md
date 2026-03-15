<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMCOS Function

The `IMCOS` function in Excel returns the **cosine** of a given complex number. It is specifically designed to handle
calculations involving complex numbers in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary
part.

This function is particularly useful in advanced mathematical and engineering applications, especially when performing
trigonometric operations in the domain of complex numbers.

### Key Features of IMCOS:

- Computes the **cosine** of a complex number.
- Handles inputs in either text string format (`"a+bi"`) or via cell references containing complex numbers.
- Returns a complex number as a result.
- Extends the concept of cosine from real numbers to complex numbers, leveraging formulas from advanced mathematics.

### Syntax:

```plaintext
IMCOS(inumber)
```

- **inumber**: The complex number for which you want to compute the cosine. This can be provided as:
    - A text string like `"3+4i"`.
    - A reference to a cell containing a valid complex number.
    - The output result of functions like `COMPLEX`.

### Formula and Calculation:

For a complex number `z = a+bi`, the cosine is calculated using the formula:

```plaintext
cos(z) = cos(a) * cosh(b) - i * sin(a) * sinh(b)
```

Where:

- **a** is the real part of `z`.
- **b** is the imaginary part of `z`.
- `cos`, `sin` are standard trigonometric functions.
- `cosh`, `sinh` are hyperbolic functions.

### Examples:

1. **Cosine of a Complex Number**:  
   `=IMCOS("1+2i")`  
   For the complex number `1+2i`, the returned value is:  
   **Result**: ~`2.03272300702 - 3.05189779915i`

2. **Use a Reference to a Complex Number**:  
   If cell `A1` contains `"0-3i"`, then:  
   `=IMCOS(A1)`  
   Returns the cosine of `0-3i`:  
   **Result**: ~`10.06766199578`

3. **Cosine of a Purely Real Number**:  
   `=IMCOS("4")`  
   For a purely real number `4`, the cosine is the same as the standard cosine function:  
   **Result**: ~`-0.65364362086`

4. **Cosine of a Purely Imaginary Number**:  
   `=IMCOS("0+2i")`  
   For a purely imaginary number, the result involves hyperbolic trigonometric functions:  
   **Result**: ~`-3.76219569108`

### Notes:

- If **inumber** is not a valid complex number, the function will return a `#NUM!` error.
- Complex numbers in Excel can be created using the `COMPLEX(real_num, imaginary_num)` function. For example:  
  `=COMPLEX(3, 4)` produces the complex number `3+4i`.

### Applications:

- **Mathematics**: Extends cosine operations into the complex plane for advanced calculations.
- **Engineering**: Useful in signal processing, control systems, and other fields where phasor and trigonometric
  representations involve complex numbers.
- **Physics**: Appears in wave mechanics and other disciplines dealing with periodic or harmonic phenomena.

### Related Functions:

- **IMSIN**: Returns the sine of a complex number.  
  Example: `=IMSIN("1+2i")` → ~`3.1657785132 + 1.95960104142i`
- **IMEXP**: Returns the exponential of a complex number.  
  Example: `=IMEXP("1+2i")` → ~`-1.13120438376 + 2.47172667200i`
- **IMCOSH**: Returns the hyperbolic cosine of a complex number.  
  Example: `=IMCOSH("1+2i")` → ~`5.03269379344 - 3.05189779915i`
- **IMREAL**: Extracts the real part of a complex number.  
  Example: `=IMREAL("3+4i")` → `3`

### Summary:

The `IMCOS` function adds powerful functionality to Excel for working in the complex domain. By enabling the calculation
of the cosine of complex numbers, it supports applications in various scientific and engineering fields. Whether using
it to model waveforms, solve equations, or process signals, the `IMCOS` function is a valuable tool in the Excel
toolkit.