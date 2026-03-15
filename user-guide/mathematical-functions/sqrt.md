<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SQRT(number)

- **number**: The number for which you want to calculate the square root. This must be a non-negative numeric value.

### Description:

The `SQRT` function returns the square root of a given number. The square root of a number is a value that, when
multiplied by itself, gives the original number. For example:

    SQRT(number) = √number

### Examples:

1. `=SQRT(4)` would return `2` because the square root of 4 is 2.
2. `=SQRT(9)` would return `3` because the square root of 9 is 3.
3. `=SQRT(0)` would return `0` because the square root of 0 is 0.
4. `=SQRT(1)` would return `1` because the square root of 1 is 1.
5. `=SQRT(2)` would return approximately `1.414213` because the square root of 2 is an irrational number.

### Notes:

- The `SQRT` function only works with non-negative numbers. If you provide a negative value, Excel will return a `#NUM!`
  error.
- It is the inverse operation of squaring a number (x²). For example, if `x = 3`, then `SQRT(9) = 3`.
- The function is widely used in mathematical, statistical, and engineering calculations.
- The result of the `SQRT` function is always a non-negative value.