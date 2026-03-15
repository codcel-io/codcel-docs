<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GCD Function

The `GCD` function in Excel calculates the greatest common divisor (GCD) of two or more integers. The GCD is the largest integer that can evenly divide all the given numbers without leaving a remainder.

### Syntax:

    GCD(number1, [number2], ...)

- **number1**: The first number for which you want to calculate the greatest common divisor.
- **number2**, ... (optional): Additional numbers for the calculation. You can include up to 255 numbers.

### Key Characteristics:

- The function works only with integers. If any number is not an integer, Excel automatically truncates it to an integer.
- If any input is zero, the GCD of the remaining numbers is returned.
- If all inputs are zero, the function returns `0`.
- The `GCD` function is useful in mathematical and computational tasks, such as simplifying fractions or finding common factors.

### Examples:

1. `=GCD(8, 12)`  
   Returns `4`, as `4` is the largest number that divides both `8` and `12`.

2. `=GCD(28, 35, 42)`  
   Returns `7`, as `7` is the largest number that divides `28`, `35`, and `42`.

3. `=GCD(18, 0)`  
   Returns `18`, since any number's GCD with `0` is the number itself.

4. `=GCD(0, 0)`  
   Returns `0`, as the GCD of two zeros is undefined and defaults to `0`.

5. `=GCD(3.9, 2.4)`  
   Returns `1`, as Excel truncates the numbers to `3` and `2`, and the largest divisor of `3` and `2` is `1`.

### Usage Notes:

- If any of the arguments are negative, the function treats them as positive for the calculation.
- Non-numeric inputs will result in an error.
- The `GCD` function is particularly valuable in tasks like reducing ratios, simplifying fractions, or determining shared divisors in data analysis.