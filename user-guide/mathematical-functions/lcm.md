<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LCM Function

The `LCM` function in Excel is used to calculate the Least Common Multiple (LCM) of integers. The LCM is the smallest
positive integer that is divisible by all the provided numbers. This function is particularly useful in scenarios
involving fractions, scheduling, or finding common intervals.

### Syntax:

    LCM(number1, [number2], ...)

- **number1, number2, ...**: Integer values (or references to cells containing integers) for which you want to find the
  Least Common Multiple. You can input up to 255 arguments in modern versions of Excel.

### Examples:

1. `=LCM(4, 5)`  
   Returns `20`, as `20` is the smallest number divisible by both `4` and `5`.

2. `=LCM(3, 6, 9)`  
   Returns `18`, since `18` is the smallest positive number divisible by `3`, `6`, and `9`.

3. `=LCM(A1:A3)`  
   If `A1=8`, `A2=12`, and `A3=15`, the function returns `120`.

4. `=LCM(7, 11)`  
   Returns `77`, as these numbers share no common factors except `1`.

5. `=LCM(10, 5, 20)`  
   Returns `20`, as `20` is divisible by `10`, `5`, and itself.

### Usage Notes:

- All provided arguments must be integers or references to cells containing integers. If a non-integer or negative
  number is included, Excel will convert it to its absolute integer value.
- If any argument evaluates to `0`, the result will always be `0`.
- The `LCM` function is helpful in mathematical computations such as finding a common denominator in fractions, or when
  synchronizing processes or events with different intervals.