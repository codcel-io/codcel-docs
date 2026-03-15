<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BIN2HEX Function

The `BIN2HEX` function in Excel converts a **binary number** to its **hexadecimal equivalent**.  
This function is valuable in scenarios that require binary-to-hexadecimal conversions, such as computer science, digital
systems, or programming.

### Key Features of BIN2HEX:

- Converts a binary number (base 2) into a hexadecimal number (base 16).
- Handles both **positive** and **negative** binary numbers:
    - For binary numbers up to 10 bits, the leftmost bit is the **sign bit**.
    - A `1` in the leftmost bit represents a **negative number** using **two's complement notation**.
    - A `0` in the leftmost bit indicates a positive number.

### Syntax:

```plaintext
BIN2HEX(number, [places])
```

- **number**: The binary number to convert.
    - Must be supplied as a **string** (enclosed in quotation marks) or as a numeric value with up to 10 characters in
      binary format.
    - If the binary number exceeds 10 characters, Excel returns a `#NUM!` error.
- **places** *(optional)*: Specifies the number of characters in the hexadecimal result.
    - If the result has fewer characters than the value specified, leading zeroes are added.
    - If omitted, Excel uses the minimum number of characters necessary.

### Examples:

1. **Convert a Positive Binary Number to Hexadecimal**:  
   `=BIN2HEX("1011")`  
   Converts the binary number `1011` to its hexadecimal equivalent.  
   **Result**: `B`

2. **Convert a Negative Binary Number to Hexadecimal**:  
   `=BIN2HEX("1111111011")`  
   Converts the 10-bit binary number `1111111011` (two's complement representation) to its hexadecimal equivalent.  
   **Result**: `FFB`

3. **Add Leading Zeroes to the Hexadecimal Result**:  
   `=BIN2HEX("101", 4)`  
   Converts the binary number `101` to its hexadecimal equivalent and pads the result to 4 characters.  
   **Result**: `0005`

4. **Invalid Binary Number**:  
   `=BIN2HEX("110011001010")`  
   Returns an error because the binary number exceeds the 10-character limit.  
   **Result**: `#NUM!`

### Notes:

- **Binary Input Limitations**:
    - The binary number must not exceed 10 bits (including the sign bit).
    - Valid binary digits are solely `0` and `1`. Anything else results in an error (`#NUM!` or `#VALUE!`).

- **Sign Bit**:
    - For binary numbers with fewer than 10 digits, the leftmost bit is treated as the sign bit, affecting whether the
      result is positive or negative.

- **Optional Argument**:
    - The `places` argument simply pads the result with leading zeroes and does not affect the actual number.

- **Error Values**:
    - `#VALUE!`: The input is not a valid binary number.
    - `#NUM!`: The binary number is too large or invalid for conversion.

### Applications:

- **Use Case**:  
  The `BIN2HEX` function is commonly used in fields such as programming and computer engineering, where hexadecimal
  numbers are preferred for compactly representing binary data.

- **Complementary Functions**:
    - **DEC2HEX**: Converts decimal numbers to hexadecimal.
    - **BIN2DEC**: Converts binary numbers to decimal.
    - **BIN2OCT**: Converts binary numbers to octal.