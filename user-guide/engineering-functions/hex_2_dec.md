<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## HEX2DEC Function

The `HEX2DEC` function in Excel converts a hexadecimal number to its decimal equivalent. This function is useful for
tasks that involve transitioning between different numeric systems, particularly for data analysis, engineering, or
programming.

### Key Features of HEX2DEC:

- Converts a **hexadecimal** number (base 16) into its **decimal** equivalent (base 10).
- Supports both positive and negative hexadecimal numbers.
- Useful for working with encoded values, memory addresses, and engineering calculations.

### Syntax:

```plaintext
HEX2DEC(number)
```

- **number**: The hexadecimal number you want to convert. This is the only required argument and can include up to 10
  characters (40 bits), including a minus sign (`-`) for negatives.

### Examples:

1. **Convert a Positive Hexadecimal Number**:  
   `=HEX2DEC("A")`  
   Converts the hexadecimal number `A` (10 in decimal).  
   **Result**: `10`

2. **Convert a Larger Hexadecimal Number**:  
   `=HEX2DEC("1F4")`  
   Converts the hexadecimal number `1F4` (500 in decimal).  
   **Result**: `500`

3. **Convert a Negative Hexadecimal Number**:  
   `=HEX2DEC("-1E")`  
   Converts the hexadecimal number `-1E` to its decimal equivalent.  
   **Result**: `-30`

### Notes:

- If the **number** argument contains more than 10 characters or is not a valid hexadecimal value, `HEX2DEC` returns a
  `#NUM!` error.
- Non-hexadecimal characters (other than the valid hex digits `0-9` and `A-F`, or the leading `-` sign for negatives)
  will trigger a `#VALUE!` error.
- Negative hexadecimal numbers are interpreted using two's complement representation.

### Applications:

- **Data Conversion**: Translate hexadecimal values into decimal for further analysis or reporting.
- **Programming**: Decode hexadecimal values from memory dumps or low-level coding tasks into readable decimal values.
- **Engineering**: Convert hexadecimal representations used in hardware or protocols into decimal equivalents for easier
  understanding.

### Related Functions:

- **HEX2BIN**: Converts a hexadecimal number to its binary equivalent.  
  Example: `=HEX2BIN("A")` → `1010`
- **HEX2OCT**: Converts a hexadecimal number to its octal equivalent.  
  Example: `=HEX2OCT("A")` → `12`
- **DEC2HEX**: Converts a decimal number to hexadecimal.  
  Example: `=DEC2HEX(15)` → `F`

### Summary:

The `HEX2DEC` function enables quick and error-free conversion of hexadecimal numbers into their decimal equivalents.
Its straightforward syntax makes it a vital tool for anyone who needs to work with multiple numbering systems, from
programmers to engineers.