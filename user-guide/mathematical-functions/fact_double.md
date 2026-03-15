<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FACTDOUBLE Function

The `FACTDOUBLE` function in Excel calculates the double factorial of a number. A double factorial of a number is the
product of all integers from the specified number down to 1 that have the same parity (even or odd) as the number
itself.

### Syntax:

    FACTDOUBLE(number)

- **number**: The non-negative number for which you want to calculate the double factorial. If the number is not an
  integer, it is truncated.

### Examples:

1. `=FACTDOUBLE(6)` would return `48`, since the double factorial of 6 is `6 * 4 * 2 = 48`.
2. `=FACTDOUBLE(7)` would return `105`, as the double factorial of 7 is `7 * 5 * 3 * 1 = 105`.
3. `=FACTDOUBLE(0)` returns `1`, because the double factorial of 0 is defined as 1.
4. `=FACTDOUBLE(1)` also returns `1`, since the double factorial of 1 is `1`.

### Usage Notes:

- The `FACTDOUBLE` function can handle only non-negative numbers. Providing a negative number will result in an error.
- Fractional numbers are truncated to integers before the function is applied.
- The double factorial grows at a slower rate compared to a standard factorial but still can become very large quickly
  for larger inputs. Ensure your results do not exceed Excel's numeric limits.
- Double factorials are often used in combinatorics, physics, and mathematical problems involving specific types of
  series or sequences.

> **Tip**: The `FACTDOUBLE` function is useful when working with problems involving alternate terms in factorial series,
> and it can simplify calculations involving only odd or even terms!