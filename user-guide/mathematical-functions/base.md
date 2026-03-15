<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BASE Function

The `BASE` function in Excel is used to convert a number into a text representation in a specified base or numeral
system (radix), such as binary, octal, decimal, or hexadecimal.

### Syntax:

    BASE(number, radix, [min_length])

- **number**: This is a required argument. It specifies the positive integer you want to convert into another base. It
  must be non-negative and less than 2^53.
- **radix**: This is a required argument that specifies the base (radix) to which the number should be converted. It
  must be an integer between 2 and 36.
- **min_length**: This is an optional argument. It specifies the minimum length of the resulting text. If the converted
  text representation of the number is shorter than `min_length`, it will be padded with leading zeros to meet the
  specified length.

### Examples:

1. `=BASE(15, 2)`  
   Converts the decimal number 15 into binary (base 2).  
   **Result**: `1111`

2. `=BASE(255, 16)`  
   Converts the decimal number 255 into hexadecimal (base 16).  
   **Result**: `FF`

3. `=BASE(10, 8, 4)`  
   Converts the decimal number 10 into octal (base 8) and ensures the result has at least 4 characters by padding with
   leading zeros.  
   **Result**: `0012`

4. `=BASE(100, 5)`  
   Converts the decimal number 100 into base 5.  
   **Result**: `400`

### Notes:

- The `BASE` function is particularly useful for tasks requiring numeral system conversions, such as converting numbers
  to binary or hexadecimal for mathematical or programming purposes.
- If the `number` is negative, or if `radix` is outside the supported range (2–36), the function will return a `#NUM!`
  error.
- If `min_length` is not specified, the function will return the shortest possible text for the converted number.

> **Tip**: The `BASE` function provides an easy way to visualize numbers in different numeral systems, which can be
beneficial in fields like computer science and engineering.