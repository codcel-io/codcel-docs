<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## COT Function

The `COT` function in Excel is used to calculate the **cotangent** of a given angle. The cotangent of an angle is
defined as the reciprocal of the tangent.

Mathematically, it can be expressed as:

    COT(x) = 1 / TAN(x)

This function is useful in trigonometry, geometry, and mathematical analysis.

### Syntax:

    COT(number)

- **number**: This is a required argument. It specifies the angle in radians for which the cotangent is to be
  calculated.

### Key Points:

- The `COT` function expects the angle to be in **radians**. If your angle is in degrees, you need to convert it to
  radians first. You can use the `RADIANS` function to perform the conversion. For example, `=COT(RADIANS(45))`.
- If the angle is zero or a multiple of π (e.g., 0, π, 2π), the tangent becomes undefined, and as a result, the `COT`
  function will return a `#DIV/0!` error.

### Examples:

1. `=COT(PI()/4)`  
   Calculates the cotangent of π/4 radians (45 degrees).  
   **Result**: `1`

2. `=COT(PI()/3)`  
   Calculates the cotangent of π/3 radians (60 degrees).  
   **Result**: `0.57735`

3. `=COT(RADIANS(30))`  
   Converts 30 degrees to radians and then computes its cotangent.  
   **Result**: `1.73205`

### Notes:

- Ensure that the angle is provided in radians for accurate results. Use the `RADIANS` function to convert degrees if
  needed.
- If `number` is a multiple of π, Excel will return a `#DIV/0!` error because the tangent is undefined at these angles.

> **Tip**: Use the `COT` function when working with cotangents in mathematical and geometric calculations. Always
> double-check the input to confirm whether it is in radians or degrees, and convert accordingly.