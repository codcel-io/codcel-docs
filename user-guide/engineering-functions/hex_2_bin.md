<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## HEX2BIN Function

The `HEX2BIN` function in Excel converts a hexadecimal number to its binary equivalent. This is particularly useful when
working with engineering, computing, or other technical tasks that require conversions between number systems.

### Key Features of HEX2BIN:

- Converts a **hexadecimal** number (base 16) to a **binary** number (base 2).
- Supports both positive and negative hexadecimal numbers.
- Allows the binary result to be padded with leading zeroes up to a specified number of characters.

### Syntax:

```plaintext
HEX2BIN(number, [places])
```

- **number**: The hexadecimal number you want to convert. This is a required argument and can include up to 10
  characters (40 bits), including a minus sign for negatives.
- **places**: (Optional) The number of characters to pad the binary result with leading zeroes. If omitted, Excel uses
  the minimal number of characters necessary to represent the binary equivalent.

### Examples:

1. **Convert a Positive Hexadecimal Number**:  
   `=HEX2BIN("F")`  
   Converts the hexadecimal number `F` (15 in decimal) to binary.  
   **Result**: `1111`

2. **Convert a Negative Hexadecimal Number**:  
   `=HEX2BIN("-1")`  
   Converts the hexadecimal number `-1` to its binary equivalent in 10 bits.  
   **Result**: `1111111111`

3. **Pad with Leading Zeroes**:  
   `=HEX2BIN("F", 8)`  
   Converts `F` and pads the result to 8 characters.  
   **Result**: `00001111`

4. **Use a Larger Hexadecimal Number**:  
   `=HEX2BIN("1A")`  
   Converts the hexadecimal value `1A` (26 in decimal) to binary.  
   **Result**: `11010`

### Notes:

- If the **number** argument contains more than 10 characters or is not a valid hexadecimal value, `HEX2BIN` returns a
  `#NUM!` error.
- If the **places** argument is provided and results in truncation or is non-numeric, the function returns a `#VALUE!`
  error.
- Negative numbers are represented using two's complement binary notation.
- If the **places** value is too small to fit the binary result, Excel will return a `#NUM!` error.

### Applications:

- **Engineering**: Used to convert hexadecimal representations into binary when designing circuits or debugging
  hardware.
- **Programming**: Helpful for translating hexadecimal numbers into binary for low-level operations, such as bitwise
  manipulations.
- **Data Analysis**: Enables conversions between number systems for tasks involving unique identifiers, memory
  addresses, or encoded values.

### Related Functions:

- **HEX2DEC**: Converts a hexadecimal number to a decimal number.  
  Example: `=HEX2DEC("F")` → `15`
- **BIN2HEX**: Converts a binary number to its hexadecimal equivalent.  
  Example: `=BIN2HEX("1111")` → `F`
- **DEC2BIN**: Converts a decimal number to binary.  
  Example: `=DEC2BIN(9)` → `1001`

### Summary:

The `HEX2BIN` function simplifies the conversion from hexadecimal to binary, making numeric system transformations
easier in spreadsheet calculations. Its features for handling both positive and negative numbers, as well as
customizable padding, make it a versatile tool for technical computations across various fields.