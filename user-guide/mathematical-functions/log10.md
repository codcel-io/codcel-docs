<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOG10 Function

The `LOG10` function in Excel is used to calculate the base-10 logarithm of a given number. This is the power to which the number 10 must be raised to equal the specified number.

### Syntax:

    LOG10(number)

- **number**: The positive numeric value for which you want to calculate the base-10 logarithm.

### Examples:

1. `=LOG10(1000)`  
   Returns `3`, because `10^3 = 1000`.

2. `=LOG10(100)`  
   Returns `2`, because `10^2 = 100`.

3. `=LOG10(1)`  
   Returns `0`, because `10^0 = 1`.

4. `=LOG10(0.1)`  
   Returns `-1`, because `10^-1 = 0.1`.

5. `=LOG10(10)`  
   Returns `1`, because `10^1 = 10`.

### Usage Notes:

- The **number** must be positive; otherwise, the function will return a `#NUM!` error.
- If the **number** is `0` or a negative value, Excel will display an error as the logarithm is undefined in such cases.
- The `LOG10` function is particularly useful in scientific, engineering, and financial applications where logarithmic calculations are necessary, such as measuring growth rates, decibel levels, or pH values.
- For logarithms with other bases, consider using the `LOG` function with the base specified explicitly.