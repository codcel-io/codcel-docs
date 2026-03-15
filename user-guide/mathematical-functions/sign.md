<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SIGN(number)

- **number**: A numeric value whose sign you want to determine. This can be positive, negative, or zero.

### Description:

The `SIGN` function in Excel returns the sign of a number. It indicates whether the number is positive, negative, or
zero, and returns:

- `1` if the number is positive
- `-1` if the number is negative
- `0` if the number is zero

### Examples:

1. `SIGN(10)` would return `1` because `10` is positive.
2. `SIGN(-5.5)` would return `-1` because `-5.5` is negative.
3. `SIGN(0)` would return `0` because the number is zero.
4. `SIGN(-0.001)` would return `-1` because even small negative values are treated as negative.

### Notes:

- The Rust implementation provided uses the `f64` data type for the input and returns an `i32` value to match the
  results of the `SIGN` function in Excel.
- This implementation can handle both integer and floating-point numbers as long as they are converted to `f64`.
- If the input is `NaN` or infinity (`f64::NAN` or `f64::INFINITY`), you might want to handle these cases separately
  based on your application's requirements.