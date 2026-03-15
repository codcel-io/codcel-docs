<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## OCT2BIN Function

The `OCT2BIN` function in Excel converts an octal number (base 8) to its binary equivalent (base 2). This function is
useful in fields such as engineering, computing, and data analysis where conversions between number systems are
frequently required.

### Key Features of OCT2BIN:

- Converts an **octal** number to a **binary** number.
- Supports conversions for both positive and negative octal numbers.
- Allows the binary result to be padded with leading zeroes up to a specified number of characters.

### Syntax:

```plaintext
OCT2BIN(number, [places])
```

- **number**: The octal number you want to convert. This is a required argument.
- **places**: (Optional) The number of characters to pad the binary result with leading zeroes. If omitted, Excel uses
  the minimal number of characters necessary.

### Examples:

1. **Convert a Positive Octal Number**:  
   `=OCT2BIN(7)`  
   Converts the octal number `7` (7 in decimal) to binary.  
   **Result**: `111`

2. **Convert a Negative Octal Number**:  
   `=OCT2BIN("-7")`  
   Converts the octal number `-7` to its binary equivalent in 10 bits.  
   **Result**: `1111111001`

3. **Pad with Leading Zeroes**:  
   `=OCT2BIN(7, 8)`  
   Converts the octal number `7` and pads the result to 8 characters.  
   **Result**: `00000111`

4. **Use a Larger Octal Number**:  
   `=OCT2BIN(17)`  
   Converts the octal number `17` (15 in decimal) to binary.  
   **Result**: `1111`

### Notes:

- If the **number** is not a valid octal number or contains invalid characters, `OCT2BIN` will return a `#NUM!` error.
- If the **places** argument is provided and results in truncation or is non-numeric, the function returns a `#VALUE!`
  error.
- Negative numbers are represented in two's complement binary notation.
- If the **places** value is too small to accommodate the binary result, Excel will return a `#NUM!` error.

### Applications:

- **Engineering**: Used to convert octal representations to binary when analyzing systems or hardware.
- **Programming**: Helpful for translating octal numbers into binary, often used in low-level programming tasks.
- **Data Processing**: Converts octal identifiers or encoded values into a binary format for further computation.

### Related Functions:

- **OCT2DEC**: Converts an octal number to decimal.  
  Example: `=OCT2DEC(7)` → `7`
- **BIN2OCT**: Converts a binary number to its octal equivalent.  
  Example: `=BIN2OCT("111")` → `7`
- **DEC2BIN**: Converts a decimal number to binary.  
  Example: `=DEC2BIN(15)` → `1111`

### Summary:

The `OCT2BIN` function provides an efficient way to convert octal numbers into binary, simplifying system
transformations within Excel. With support for padding and the conversion of negative numbers, it is a reliable tool for
technical calculations in various disciplines.