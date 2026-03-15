<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMCOT Function

The `IMCOT` function in Excel calculates the **cotangent** of a given complex number. It is designed to handle complex
numbers represented in the form `a+bi` or `a+bj`, where `a` is the real part and `b` is the imaginary part.

This function is particularly useful in advanced mathematical and engineering applications, especially when working with
trigonometric operations involving complex numbers.

### Key Features of IMCOT:

- Computes the **cotangent** of a complex number.
- Accepts inputs as text strings (e.g., `"a+bi"`), cell references containing complex numbers, or results from other
  functions like `COMPLEX`.
- Returns a complex number as the result.

### Syntax:

```plaintext
IMCOT(inumber)
```

- **inumber**: The complex number for which you want to compute the cotangent. This can be provided as:
    - A text string such as `"2+3i"`.
    - A reference to a cell containing a valid complex number.
    - The output from the `COMPLEX` function.

### Formula and Calculation:

For a complex number `z = a+bi`, the cotangent is calculated using the formula:

```plaintext
cot(z) = cos(z) / sin(z)
```

Where:

- **cos(z)** is the trigonometric cosine of `z`.
- **sin(z)** is the trigonometric sine of `z`.
- **a** is the real part of `z`.
- **b** is the imaginary part of `z`.

### Examples:

1. **Cotangent of a Complex Number**:  
   `=IMCOT("1+2i")`  
   For the complex number `1+2i`, the returned value is:  
   **Result**: ~`0.03381282608 - 1.01479361614i`

2. **Using a Reference to a Complex Number**:  
   If cell `A1` contains `"3-4i"`, then:  
   `=IMCOT(A1)`  
   Returns the cotangent of `3-4i`:  
   **Result**: ~`0.00018756091 + 0.99935598732i`

3. **Cotangent of a Purely Real Number**:  
   `=IMCOT("3")`  
   For purely real numbers, the result is the standard cotangent:  
   **Result**: ~`-7.01525255143`

4. **Cotangent of a Purely Imaginary Number**:  
   `=IMCOT("0+2i")`  
   For purely imaginary numbers, the result is:  
   **Result**: ~`0 - 1.00067382518i`

### Notes:

- If **inumber** is not a valid complex number, the function will return a `#NUM!` error.
- Complex numbers in Excel can be created using the `COMPLEX(real_num, imaginary_num)` function. For example:  
  `=COMPLEX(5, -3)` generates the complex number `5-3i`.
- The trigonometric cotangent is undefined for cases where `sin(z) = 0`. If this occurs, the function returns a
  `#DIV/0!` error.

### Applications:

- **Mathematics**: Extends trigonometric cotangent calculations into the complex plane.
- **Engineering**: Useful in the analysis of waveforms or oscillatory systems involving complex arguments.
- **Physics**: Critical when working with complex wave representations or phase relations.

### Related Functions:

- **IMSIN**: Returns the trigonometric sine of a complex number.  
  Example: `=IMSIN("2+3i")` → ~`9.15449914662 + 4.16890695997i`
- **IMCOS**: Returns the trigonometric cosine of a complex number.  
  Example: `=IMCOS("2+3i")` → ~`-4.18962569097 - 9.10922789376i`
- **IMDIV**: Divides one complex number by another.  
  Example: `=IMDIV("3+4i", "1-2i")` → ~`-1.4 + 2.2i`

### Summary:

The `IMCOT` function enhances Excel’s capability for trigonometric computations in the complex domain. It is
particularly valuable for those working in advanced fields such as engineering, physics, and applied mathematics,
enabling the study and manipulation of cotangent functions in both real and complex planes.