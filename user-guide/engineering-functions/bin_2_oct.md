<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BIN2OCT Function

The `BIN2OCT` function in Excel converts a **binary number** to its **octal equivalent**.  
This function is particularly useful when working with binary and octal number systems, often encountered in computer
science, digital electronics, and programming.

### Key Features of BIN2OCT:

- Converts a binary number (base 2) into an octal number (base 8).
- Handles both **positive** and **negative** binary numbers:
    - For binary numbers up to 10 bits, the leftmost bit is the **sign bit**.
    - A `1` in the leftmost bit represents a **negative number** using **two's complement notation**.
    - A `0` in the leftmost bit indicates a positive number.

### Syntax:

```plaintext
BIN2OCT(number, [places])
```

- **number**: The binary number to convert.
    - Must be provided as a **string** (enclosed in quotation marks) or as a numeric value with up to 10 characters in
      binary format.
    - If the binary input exceeds 10 characters, Excel returns a `#NUM!` error.
- **places** *(optional)*: Specifies the number of characters in the octal result.
    - If the result has fewer characters than the value specified, leading zeroes are added.
    - If omitted, Excel uses the minimum number of characters necessary.

### Examples:

1. **Convert a Positive Binary Number to Octal**:  
   `=BIN2OCT("1011")`  
   Converts the binary number `1011` to its octal equivalent.  
   **Result**: `13`

2. **Convert a Negative Binary Number to Octal**:  
   `=BIN2OCT("1111111011")`  
   Converts the 10-bit binary number `1111111011` (two's complement representation) to its octal equivalent.  
   **Result**: `7777773`

3. **Add Leading Zeroes to the Octal Result**:  
   `=BIN2OCT("101", 4)`  
   Converts the binary number `101` to its octal equivalent and pads the result to 4 characters.  
   **Result**: `0005`

4. **Invalid Binary Number**:  
   `=BIN2OCT("110011001010")`  
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
  The `BIN2OCT` function is widely used in areas such as programming and digital electronics, where octal numbers are
  employed to simplify data representation derived from binary sequences.

- **Complementary Functions**:
    - **DEC2OCT**: Converts decimal numbers to octal.
    - **BIN2DEC**: Converts binary numbers to decimal.
    - **BIN2HEX**: Converts binary numbers to hexadecimal.