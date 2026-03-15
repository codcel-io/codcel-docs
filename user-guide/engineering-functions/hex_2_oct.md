<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## HEX2OCT Function

The `HEX2OCT` function in Excel converts a hexadecimal number to its octal equivalent. This function is particularly
useful in fields like programming, data analysis, and engineering for converting data between different numeric systems.

### Key Features of HEX2OCT:

- Converts a **hexadecimal** number (base 16) into an **octal** number (base 8).
- Supports both positive and negative hexadecimal numbers.
- Useful when analyzing systems or files that use hexadecimal or octal representations.

### Syntax:

```plaintext
HEX2OCT(number, [places])
```

- **number**: The hexadecimal number you want to convert. This is the only required argument.
- **[places]** (optional): The number of characters to pad the resultant octal number with zeros. If omitted, no padding
  is applied.

### Examples:

1. **Convert a Positive Hexadecimal Number**:  
   `=HEX2OCT("A")`  
   Converts the hexadecimal number `A` (10 in decimal) to its octal equivalent.  
   **Result**: `12`

2. **Convert a Larger Hexadecimal Number**:  
   `=HEX2OCT("1F4")`  
   Converts the hexadecimal number `1F4` (500 in decimal) to octal.  
   **Result**: `764`

3. **Convert a Negative Hexadecimal Number**:  
   `=HEX2OCT("-1F")`  
   Converts the hexadecimal number `-1F` to its octal equivalent using two's complement.  
   **Result**: `777761`

4. **Use the `places` Argument for Padding**:  
   `=HEX2OCT("A", 5)`  
   Converts `A` (10 in decimal) to octal and pads it to 5 characters.  
   **Result**: `00012`

### Notes:

- If the **number** argument is not a valid hexadecimal value, `HEX2OCT` returns a `#NUM!` error.
- The **[places]** argument must be a positive integer, or Excel will return a `#VALUE!` error.
- Negative hexadecimal values are interpreted using two's complement representation.

### Applications:

- **Data Conversion**: Facilitates conversion of hexadecimal values to octal for data processing or visualization.
- **Programming**: Useful when dealing with systems that operate on octal numbers (e.g., file permissions in
  Unix/Linux).
- **Engineering**: Helps engineers working with hardware that uses octal numbering systems.

### Related Functions:

- **HEX2BIN**: Converts a hexadecimal number to its binary equivalent.  
  Example: `=HEX2BIN("A")` → `1010`
- **HEX2DEC**: Converts a hexadecimal number to decimal.  
  Example: `=HEX2DEC("A")` → `10`
- **DEC2OCT**: Converts a decimal number to its octal equivalent.  
  Example: `=DEC2OCT(10)` → `12`

### Summary:

The `HEX2OCT` function provides a simple way to convert hexadecimal numbers into octal format. This makes it a practical
tool when working with systems or protocols that rely on the octal numbering system, especially for programming,
engineering, and numerical analysis.