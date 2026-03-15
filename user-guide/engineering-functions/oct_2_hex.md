<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## OCT2HEX Function

The `OCT2HEX` function in Excel converts an octal number (base 8) to its hexadecimal equivalent (base 16). This function
is useful in areas such as computer science and digital systems, where conversions between number systems are often
necessary.

### Key Features of OCT2HEX:

- Converts an **octal** number to a **hexadecimal** number.
- Supports both positive and negative octal numbers.
- Allows specifying the desired length of the resulting hexadecimal output.

### Syntax:

```plaintext
OCT2HEX(number, [places])
```

- **number**: The octal number you want to convert. This is a required argument.
- **places**: An optional argument that specifies the number of characters in the hexadecimal result. If the result is
  shorter than the specified number, leading zeros are added. If omitted, the result will have only the necessary length
  to represent the hexadecimal value.

### Examples:

1. **Convert a Positive Octal Number to Hexadecimal**:  
   `=OCT2HEX(10)`  
   Converts the octal number `10` (8 in decimal) to its hexadecimal equivalent.  
   **Result**: `8`

2. **Convert a Larger Octal Number to Hexadecimal**:  
   `=OCT2HEX(77)`  
   Converts the octal number `77` (63 in decimal) to hexadecimal.  
   **Result**: `3F`

3. **Convert a Negative Octal Number to Hexadecimal**:  
   `=OCT2HEX("-10")`  
   Converts the negative octal number `-10` (-8 in decimal) to its hexadecimal equivalent.  
   **Result**: `FFF8`

4. **Specify the Length of the Hexadecimal Result**:  
   `=OCT2HEX(10, 4)`  
   Converts the octal number `10` (8 in decimal) to hexadecimal with 4 characters by padding with leading zeros.  
   **Result**: `0008`

### Notes:

- If the **number** is not a valid octal value or includes invalid characters, Excel will return a `#NUM!` error.
- **places** must be a positive integer. If the specified length is not large enough to hold the result, Excel will
  return a `#NUM!` error.
- Negative octal numbers are supported and properly converted into their hexadecimal values using two's complement
  representation.

### Applications:

- **Digital Systems**: Useful for working with data representations where octal and hexadecimal systems are common.
- **Programming and Debugging**: Assists in converting numerical data between octal and hexadecimal when working with
  memory addresses, file permissions, or low-level data processing.
- **Data Analysis**: Enables accurate conversions for interpreting encoded data.

### Related Functions:

- **HEX2OCT**: Converts a hexadecimal number to its octal equivalent.  
  Example: `=HEX2OCT("3F")` → `77`
- **DEC2HEX**: Converts a decimal number to hexadecimal.  
  Example: `=DEC2HEX(63)` → `3F`
- **HEX2DEC**: Converts a hexadecimal number to its decimal equivalent.  
  Example: `=HEX2DEC("3F")` → `63`

### Summary:

The `OCT2HEX` function in Excel simplifies the process of converting octal numbers to hexadecimal. With support for
optional length specification and compatibility with both positive and negative numbers, this function is a versatile
tool for data conversion in technical and engineering fields.