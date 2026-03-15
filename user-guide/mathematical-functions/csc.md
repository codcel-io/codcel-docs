<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CSC Function

The `CSC` function in Excel is used to calculate the **cosecant** of a given angle in radians. The cosecant of an angle
is defined as the reciprocal of the sine of the angle.

Mathematically, it can be expressed as:

    CSC(x) = 1 / SIN(x)

where `SIN(x)` is the sine of the angle `x`.

This function is useful in trigonometry and various mathematical, scientific, and engineering computations.

### Syntax:

    CSC(number)

- **number**: This is a required argument. It specifies the angle (in radians) for which the cosecant should be
  calculated.

### Key Points:

- The `CSC` function operates on **real numbers**, representing angles in radians.
- If the value of `number` is a multiple of `π` (e.g., `0`, `π`, `2π`), where the sine is `0`, the `CSC` function will
  result in a `#DIV/0!` error, as division by zero is undefined.
- To use degrees instead of radians, convert the angle to radians first using the `RADIANS` function:
  `RADIANS(angle_in_degrees)`.

### Examples:

1. `=CSC(PI()/2)`  
   Calculates the cosecant of `π/2` radians.  
   **Result**: `1`

2. `=CSC(PI()/6)`  
   Calculates the cosecant of `π/6` radians.  
   **Result**: `2`

3. `=CSC(PI())`  
   As the sine of `π` is `0`, the `CSC` function will throw a divide-by-zero error.  
   **Result**: `#DIV/0!`

4. `=CSC(RADIANS(30))`  
   Converts `30` degrees to radians and calculates its cosecant.  
   **Result**: `2`

### Notes:

- Ensure the input `number` is in **radians**, not degrees. Use the `RADIANS` function for converting degrees to radians
  if necessary.
- The `CSC` function will throw a `#DIV/0!` error if the sine of the input angle is `0`, as division by zero is
  undefined.

> **Tip**: Use the `CSC` function when dealing with reciprocal trigonometric functions in your calculations. Be cautious
of input angles that result in undefined behavior.