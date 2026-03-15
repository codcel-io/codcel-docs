<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ATANH Function

The `ATANH` function in Excel returns the inverse hyperbolic tangent of a number. Essentially, it computes the value whose hyperbolic tangent is the specified number.

### Syntax:

    ATANH(number)


- **number**: This is a required argument. The numeric value for which you want to find the inverse hyperbolic tangent. The value must be between -1 (exclusive) and 1 (exclusive).

### Examples:

1. `=ATANH(0.5)` would return a value approximately equal to 0.5493.
2. `=ATANH(0)` would give a result of 0, as the inverse hyperbolic tangent of 0 is 0.
3. `=ATANH(A1)` would return the inverse hyperbolic tangent of the number in cell A1, provided the value in A1 is within the valid range.

> **Note**: The `ATANH` function is employed in hyperbolic trigonometry. While hyperbolic functions might be less commonly encountered than their circular counterparts (like `SIN`, `COS`, and `TAN`), they are beneficial in specific areas of mathematics and engineering.