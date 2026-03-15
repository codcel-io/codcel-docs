<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IMARGUMENT Function

The `IMARGUMENT` function in Excel calculates the **angle, or argument, of a complex number** in radians. The argument
of a complex number represents the angle formed by the complex number in the complex plane with respect to the positive
x-axis. This function is widely used in fields such as mathematics, engineering, and physics.

### Key Features of IMARGUMENT:

- Calculates the **angle (argument)** of a complex number.
- Works with complex numbers in the form `a+bi`, `a-bi`, or `a+bj`, where `a` is the real part and `b` is the imaginary
  part.
- Returns the result in **radians**.
- Useful for analyzing the polar form of complex numbers.

### Syntax:

```plaintext
IMARGUMENT(inumber)
```

- **inumber**: The complex number for which you want to calculate the argument. It should either be a text string like
  `"3+4i"`, or a reference pointing to a cell containing the complex number.

### Formula:

The argument (angle θ) for a complex number `a+bi` is calculated using:

```plaintext
θ = ATAN2(b, a)
```

Where:

- **a** is the real part of the complex number.
- **b** is the imaginary part of the complex number.

**Note:** The `ATAN2` function calculates the arctangent of the quotient of its arguments, taking into account the
correct quadrant of the angle.

### Examples:

1. **Calculate the Argument of a Complex Number**:  
   `=IMARGUMENT("3+4i")`  
   For the complex number `3+4i`, the argument is calculated as:  
   **Result**: `0.93` radians (approximately, since `ATAN2(4, 3) ≈ 0.93`).

2. **Use a Reference to a Complex Number**:  
   If cell `A1` contains `"5-12i"`, then:  
   `=IMARGUMENT(A1)`  
   Calculates the argument of `5-12i`.  
   **Result**: `-1.17` radians (since `ATAN2(-12, 5) ≈ -1.17`).

3. **Argument of a Purely Real Number**:  
   `=IMARGUMENT("7")`  
   For a purely real number, the argument is `0` radians if it is positive and `π` radians if negative.  
   **Result**: `0` (since no imaginary component exists).

4. **Argument of a Purely Imaginary Number**:  
   `=IMARGUMENT("0+6i")`  
   For a purely imaginary number, the argument is `π/2` radians if the number is positive, and `-π/2` if negative.  
   **Result**: `1.57` radians (approximately, for `π/2`).

### Notes:

- The returned angle is always in **radians**. To convert the result to degrees, use the `DEGREES` function:
  ```plaintext
  =DEGREES(IMARGUMENT("3+4i"))
  ```
  This converts the radians result to degrees.
- If **inumber** is not a valid complex number, the function returns a `#NUM!` error.
- Complex numbers in Excel can be created using the `COMPLEX` function:
  `=COMPLEX(real_num, imaginary_num)`.

### Applications:

- **Electrical Engineering**: Used in analyzing phasors or impedances in AC circuits.
- **Mathematics**: Helpful for expressing complex numbers in polar form.
- **Physics**: Analyze waveforms or oscillatory behaviors represented by complex numbers.

### Related Functions:

- **IMABS**: Returns the absolute value (magnitude) of a complex number.  
  Example: `=IMABS("3+4i")` → `5`
- **IMREAL**: Returns the real part of a complex number.  
  Example: `=IMREAL("3+4i")` → `3`
- **IMAGINARY**: Returns the imaginary part of a complex number.  
  Example: `=IMAGINARY("3+4i")` → `4`
- **IMCONJUGATE**: Returns the complex conjugate of a complex number.  
  Example: `=IMCONJUGATE("3+4i")` → `3-4i`

### Summary:

The `IMARGUMENT` function is a powerful tool for analyzing the angular properties of complex numbers in mathematics,
engineering, and scientific computations. By calculating the argument in radians, it helps in understanding the
orientation of the complex number in the complex plane, making it a crucial component of polar form conversions and
other complex number operations.