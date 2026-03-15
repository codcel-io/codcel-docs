<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOG Function

The `LOG` function in Excel is used to calculate the logarithm of a number to a specified base. This function is
versatile and allows you to calculate logarithms for various bases such as 2, 10, or any other positive number.

### Syntax:

    LOG(number, [base])

- **number**: The positive numeric value for which you want to calculate the logarithm.
- **base** *(optional)*: The base of the logarithm. If omitted, the default base is `10`.

### Examples:

1. `=LOG(1000, 10)`  
   Returns `3`, because `10^3 = 1000`.

2. `=LOG(8, 2)`  
   Returns `3`, because `2^3 = 8`.

3. `=LOG(81, 3)`  
   Returns `4`, because `3^4 = 81`.

4. `=LOG(1, 10)`  
   Returns `0`, because `10^0 = 1`.

5. `=LOG(32, 2)`  
   Returns `5`, because `2^5 = 32`.

6. `=LOG(100)`  
   Returns `2`, because the default base is `10`, and `10^2 = 100`.

### Usage Notes:

- The **number** must be positive; otherwise, the function will return a `#NUM!` error.
- The **base** must be a positive number and cannot be `1`, as logarithms with those values are undefined.
- If **base** is omitted, Excel assumes a base of `10` (default logarithm base).
- Use the `LOG` function in various contexts such as mathematical, financial, or scientific computations whenever
  non-default bases are needed. For simple base-10 logarithms, you may also use the `LOG10` function.