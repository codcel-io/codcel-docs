<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DEC2HEX Function

The `DEC2HEX` function in Excel converts a decimal number (base 10) into a hexadecimal number (base 16) in text format.

### Key Features of DEC2HEX:

- Converts a decimal number into its hexadecimal representation.
- Handles both positive and negative decimal numbers.
- Widely used in fields like computer science, electronics, and digital systems to represent numbers in base 16.

### Syntax:

```plaintext
DEC2HEX(number, [places])
```

- **number**: The decimal number to be converted to hexadecimal. It must be an integer between -549,755,813,888 and
  549,755,813,887.
- **places** (optional): The number of characters to pad the hexadecimal number with. Adds leading zeros to ensure the
  result has the specified total length.

### Examples:

1. **Basic Conversion**:  
   `=DEC2HEX(255)`  
   Converts the decimal number `255` to hexadecimal.  
   **Result**: `FF`

2. **Specifying Places**:  
   `=DEC2HEX(255, 4)`  
   Converts `255` to hexadecimal and pads the result to four characters with leading zeros.  
   **Result**: `00FF`

3. **Negative Number Conversion**:  
   `=DEC2HEX(-5)`  
   Converts the decimal `-5` to hexadecimal in two's complement form.  
   **Result**: `FFFFFFFFFB`

4. **Using Larger Numbers**:  
   `=DEC2HEX(1234567890)`  
   Converts `1234567890` to hexadecimal without padding.  
   **Result**: `499602D2`

5. **Zero Padding for Larger Positive Numbers**:  
   `=DEC2HEX(16, 3)`  
   Converts the decimal `16` to hexadecimal and pads it to three places.  
   **Result**: `010`

6. **Omitting Places**:  
   `=DEC2HEX(48)`  
   Converts `48` to hexadecimal without adding any zeros.  
   **Result**: `30`

### Notes:

- **Range of Input**:  
  The `number` parameter must be between -549,755,813,888 and 549,755,813,887. Numbers outside this range return the
  `#NUM!` error.

- **Default `places` Behavior**:  
  If omitted, the result will not include padding and will return the shortest hexadecimal representation.

- **Error Handling**:
    - If `number` is non-numeric, Excel returns a `#VALUE!` error.
    - If `places` is non-numeric or less than 1, Excel also returns a `#VALUE!` error.
    - If the hexadecimal result exceeds the specified `places` length, Excel returns a `#NUM!` error.

- **Negative Numbers Representation**:  
  Negative numbers are represented in two's complement hexadecimal form, meaning they are placed in a signed 40-bit
  range.

### Applications:

- **Use Cases**:
    - Representing decimal numbers in hexadecimal for memory addresses, error codes, or color values in programming.
    - Visualizing hexadecimal data directly in Excel for system design and implementation.

- **Complementary Functions**:
    - **HEX2DEC**: Converts a hexadecimal number back to a decimal number.
    - **DEC2BIN**: Converts a decimal number to a binary number.
    - **DEC2OCT**: Converts a decimal number to an octal number.
    - **HEX2BIN**, **HEX2OCT**: Convert hexadecimal to other number systems.

### Summary:

The `DEC2HEX` function is a powerful tool in Excel for converting decimal numbers into hexadecimal representations. It
is essential for programming, scientific, and engineering applications where base 16 notation is preferred for its
compactness and ease of use.