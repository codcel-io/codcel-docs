<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MULTINOMIAL Function

The `MULTINOMIAL` function in Excel returns the ratio of the factorial of the sum of values to the product of the factorials of the values. It is used to calculate multinomial coefficients, which are useful in combinatorics and statistics.

### Syntax:

    MULTINOMIAL(number1, [number2], ...)

- **number1, number2, ...**: Numbers or values for which you want to calculate the multinomial. You can input up to 255 values.

### Examples:

1. **Basic Multinomial Calculation**  
   Formula: `=MULTINOMIAL(2, 3, 4)`  
   Returns: `1260`  
   Explanation: Multinomial is calculated as (2+3+4)! / (2! * 3! * 4!) = 1260.

2. **Multinomial with Equal Values**  
   Formula: `=MULTINOMIAL(3, 3, 3)`  
   Returns: `1680`  
   Explanation: (3+3+3)! / (3! * 3! * 3!) = 1680.

3. **Multinomial with Zeros**  
   Formula: `=MULTINOMIAL(4, 0, 2)`  
   Returns: `15`  
   Explanation: (4+0+2)! / (4! * 0! * 2!) = 15.

### Usage Notes:

- All input values must be non-negative integers; otherwise, Excel will return a `#NUM!` error.
- If any argument is non-numeric, `MULTINOMIAL` will return a `#VALUE!` error.
- The `MULTINOMIAL` function is particularly useful for multinomial expansions and combinatorial calculations in probability and statistics.