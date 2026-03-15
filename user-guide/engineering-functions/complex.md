<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COMPLEX Function

The `COMPLEX` function in Excel converts real and imaginary coefficients into a complex number in the form of `a + bi`
or `a + bj`.

A **complex number** has two parts:

- The **real part** (`a`) represents the real component.
- The **imaginary part** (`b`) is associated with the square root of `-1`, denoted as `i` (or `j` in electrical
  engineering).

### Key Features of COMPLEX:

- Simplifies the creation of complex numbers from their real and imaginary coefficients.
- Represents data in a format suitable for advanced mathematical computations.
- Used extensively in engineering, physics, and other domains involving complex numbers.

### Syntax:

```plaintext
COMPLEX(real_num, i_num, [suffix])
```

- **real_num**: The real (non-imaginary) part of the complex number.
- **i_num**: The coefficient of the imaginary part (multiplied by `i` or `j`).
- **suffix** (optional): A text value, either `"i"` (default) or `"j"`, specifying how the imaginary unit should be
  represented.

### Examples:

1. **Basic Complex Number**:  
   `=COMPLEX(3, 4)`  
   Creates the complex number `3 + 4i` with default suffix `i`.  
   **Result**: `3 + 4i`

2. **Using the `"j"` Suffix**:  
   `=COMPLEX(5, -2, "j")`  
   Specifies the suffix as `j`, creating the complex number `5 - 2j`.  
   **Result**: `5 - 2j`

3. **Zero Real Part**:  
   `=COMPLEX(0, 7)`  
   Represents a purely imaginary number `7i`.  
   **Result**: `7i`

4. **Zero Imaginary Part**:  
   `=COMPLEX(6, 0)`  
   Represents a purely real number `6`.  
   **Result**: `6`

5. **Negative Real and Imaginary Parts**:  
   `=COMPLEX(-3, -8)`  
   Creates the complex number `-3 - 8i`.  
   **Result**: `-3 - 8i`

### Notes:

- **Default Suffix**:  
  If the `suffix` parameter is omitted, Excel uses `"i"` by default.

- **Error Handling**:
    - If the `suffix` is anything other than `"i"` or `"j"`, Excel returns a `#VALUE!` error.
    - Non-numeric values for `real_num` or `i_num` result in a `#VALUE!` error.

- **Real Numbers are Supported**:  
  If `i_num` equals `0`, the resulting complex number has no imaginary component and is purely real.

### Applications:

- **Use Cases**:
    - Perform mathematical calculations on complex numbers using other Excel functions like `IMSUM`, `IMPRODUCT`, or
      `IMABS`.
    - Represent impedance in electrical engineering.
    - Model systems that use complex dynamics, such as frequency analysis or signal processing.

- **Complementary Functions**:
    - **IMSUM**: Adds two or more complex numbers.
    - **IMSUB**: Subtracts complex numbers.
    - **IMPRODUCT**: Multiplies complex numbers.
    - **IMDIV**: Divides complex numbers.
    - **IMABS**: Returns the absolute value (magnitude) of a complex number.

### Summary:

The `COMPLEX` function is a powerful tool for representing and working with complex numbers in Excel. It creates numbers
with both real and imaginary parts, paving the way for advanced mathematical and engineering applications.