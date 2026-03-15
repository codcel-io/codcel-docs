<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    TANH(number)

- **number**: The numeric value for which you want to calculate the hyperbolic tangent.

### Description:

The `TANH` function returns the hyperbolic tangent of a given number. The formula for the hyperbolic tangent is defined
as:

    TANH(number) = (e^number - e^(-number)) / (e^number + e^(-number))

Where `e` is the base of the natural logarithm (approximately 2.71828182845905). The result of `TANH` is a value between
-1 and 1.

### Examples:

1. `=TANH(0)` would return `0`, as the hyperbolic tangent of `0` is `0`.
2. `=TANH(1)` would return approximately `0.761594`, based on the formula.
3. `=TANH(-1)` would return approximately `-0.761594`, as negative inputs result in negative outputs within the same
   range.
4. `=TANH(2)` would return approximately `0.964028`, because the hyperbolic tangent approaches `1` as the input grows
   larger.
5. `=TANH(-2)` would return approximately `-0.964028`, as the hyperbolic tangent approaches `-1` for large negative
   inputs.

### Notes:

- The `TANH` function is often used in mathematical, engineering, or scientific calculations involving hyperbolic
  functions.
- The hyperbolic tangent is analogous to the `TAN` (tangent) function but relates to hyperbolic geometry.
- As the input moves towards infinity in the positive or negative direction, the result of `TANH` converges towards `1`
  or `-1`, respectively.
- The function accepts both positive and negative numeric inputs, including zero.