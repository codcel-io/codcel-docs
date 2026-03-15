<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## OCT2DEC Function

The `OCT2DEC` function in Excel converts an octal number (base 8) to its decimal equivalent (base 10). This function is
useful in areas like engineering, computing, and data analysis where conversions between number systems are frequently
needed.

### Key Features of OCT2DEC:

- Converts an **octal** number to a **decimal** number.
- Supports both positive and negative octal numbers.
- Handles valid octal numbers up to specific Excel limits.

### Syntax:

```plaintext
OCT2DEC(number)
```

- **number**: The octal number you want to convert. This is a required argument.

### Examples:

1. **Convert a Positive Octal Number**:  
   `=OCT2DEC(10)`  
   Converts the octal number `10` (8 in decimal) to its decimal equivalent.  
   **Result**: `8`

2. **Convert a Larger Octal Number**:  
   `=OCT2DEC(77)`  
   Converts the octal number `77` (63 in decimal) to decimal.  
   **Result**: `63`

3. **Convert a Negative Octal Number**:  
   `=OCT2DEC("-10")`  
   Converts the negative octal number `-10` (-8 in decimal) to its decimal equivalent.  
   **Result**: `-8`

### Notes:

- If the **number** is not a valid octal number or contains invalid characters, `OCT2DEC` will return a `#NUM!` error.
- Negative octal numbers are supported and converted properly into their decimal counterparts.
- Octal numbers may not contain digits outside the range of 0 through 7. Any inclusion of invalid digits will cause an
  error.

### Applications:

- **Engineering**: Useful for working with systems that use octal representations, such as legacy computing systems.
- **Programming**: Helps in converting file permission values represented in octal to decimal for easier understanding.
- **Data Processing**: Converts encoded octal values into decimal numbers for further analysis or calculations.

### Related Functions:

- **DEC2OCT**: Converts a decimal number to its octal equivalent.  
  Example: `=DEC2OCT(8)` → `10`
- **OCT2BIN**: Converts an octal number to binary.  
  Example: `=OCT2BIN(7)` → `111`
- **BIN2OCT**: Converts a binary number to octal.  
  Example: `=BIN2OCT("111")` → `7`

### Summary:

The `OCT2DEC` function provides a fast and reliable way to convert octal values into their decimal equivalents within
Excel. With support for negative and positive octal numbers, it is a practical tool for numerical conversions in various
technical fields.