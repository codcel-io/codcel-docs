<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FACT Function

The `FACT` function in Excel calculates the factorial of a number. A factorial of a number is the product of all integers from 1 to that number. It's denoted as `n!`, where `n` is the number, and is essential in various mathematical and statistical calculations.

### Syntax:

    FACT(number)

- **number**: The non-negative number for which you want to calculate the factorial. If the number is not an integer, it is truncated.

### Examples:

1. `=FACT(5)` would return `120`, since 5! (factorial of 5) is `1 * 2 * 3 * 4 * 5 = 120`.
2. `=FACT(3)` would return `6`, as 3! is `1 * 2 * 3 = 6`.
3. `=FACT(0)` returns `1`, because the factorial of 0 is defined as 1.

### Usage Notes:
- Factorials are commonly used in permutations and combinations, probability theory, and in various functions of algebra and calculus.
- The `FACT` function only works with non-negative numbers. If a negative number is provided, it will result in an error.
- For large numbers, the result of `FACT` can be very large and might exceed Excel's capacity for number storage, leading to an error or an overflow.

> **Note**: Factorials grow extremely rapidly with larger numbers, so it's common to encounter large outputs even for relatively small inputs in the `FACT` function.