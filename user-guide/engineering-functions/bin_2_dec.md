<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BIN2DEC Function

The `BIN2DEC` function in Excel converts a **binary number** to its **decimal equivalent**.  
This function is particularly useful in digital electronics, computer science, or any scenario requiring
binary-to-decimal conversions.

### Key Features of BIN2DEC:

- Converts a binary number (base 2) into a decimal number (base 10).
- Handles both **positive** and **negative** binary numbers:
    - If the binary number is 10 bits or fewer, the function interprets the leftmost bit as the **sign bit**.
    - A `1` in the leftmost bit (sign bit) represents a **negative number** using **two's complement notation**.
    - A `0` in the leftmost bit indicates a positive number.

### Syntax:

```plaintext
BIN2DEC(number)
```

- **number**: The binary number to be converted.
    - Must be supplied as a **string** (enclosed in quotation marks) or as a numeric value with no more than 10
      characters in binary format.
    - If the binary number has more than 10 characters, Excel returns a `#NUM!` error.

### Examples:

1. **Convert a Positive Binary Number**:  
   `=BIN2DEC("101")`  
   Converts the binary number `101` to its decimal equivalent.  
   **Result**: `5`

2. **Convert a Negative Binary Number**:  
   `=BIN2DEC("1111111011")`  
   Converts the 10-bit binary number `1111111011` (two's complement representation) to its decimal equivalent.  
   **Result**: `-5`

3. **Invalid Binary Number**:  
   `=BIN2DEC("110011001010")`  
   Returns an error because the binary number exceeds the 10-character limit.  
   **Result**: `#NUM!`

### Notes:

- **Binary Limitations**:
    - The input binary number must not exceed 10 bits (including the sign bit).
    - Valid binary digits are `0` and `1`; any other characters will result in a `#NUM!` or `#VALUE!` error.

- **Sign Bit**:
    - For a binary number with fewer than 10 digits, the leftmost bit will still be treated as the sign bit.
    - To represent large binary numbers without ambiguity, use the `BIN2DEC` function for each segment or consider
      manual calculations.

- **Error values**:
    - `#VALUE!`: Occurs if the input is not recognized as a valid binary number.
    - `#NUM!`: Occurs if the binary number exceeds 10 characters.

### Applications:

- **Use Case**: The `BIN2DEC` function is commonly used in computer systems programming, electronics engineering,  
  and cryptography, particularly for interpreting and manipulating binary data.

- **Complementary Functions**:
    - **DEC2BIN**: Converts decimal numbers to binary numbers.
    - **BIN2HEX**: Converts binary numbers to hexadecimal format.
    - **BIN2OCT**: Converts binary numbers to octal format.