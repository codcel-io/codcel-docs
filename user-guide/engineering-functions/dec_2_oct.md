<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DEC2OCT Function

The `DEC2OCT` function in Excel converts a decimal number (base 10) to an octal number (base 8), represented as text.

### Key Features of DEC2OCT:

- Converts a decimal number into its octal (base 8) representation.
- Handles both positive and negative decimal numbers.
- Useful in systems that use octal representation, such as certain digital systems or coding applications.

### Syntax:

```plaintext
DEC2OCT(number, [places])
```

- **number**: The decimal number to be converted to octal. It must be an integer between -536,870,912 and 536,870,911.
- **places** (optional): The number of characters to pad the octal number with. Adds leading zeros to the result to
  ensure it has the specified total length.

### Examples:

1. **Basic Conversion**:  
   `=DEC2OCT(8)`  
   Converts the decimal number `8` to octal.  
   **Result**: `10`

2. **Specifying Places**:  
   `=DEC2OCT(8, 3)`  
   Converts `8` to octal and pads it to three places with leading zeros.  
   **Result**: `010`

3. **Negative Number Conversion**:  
   `=DEC2OCT(-3)`  
   Converts the decimal `-3` to octal in two's complement form (signed 30-bit range).  
   **Result**: `77777777775`

4. **Zero Padding for Positive Numbers**:  
   `=DEC2OCT(16, 5)`  
   Converts `16` to octal and pads it with leading zeros to ensure the result is five characters long.  
   **Result**: `00020`

5. **Omitting Places**:  
   `=DEC2OCT(64)`  
   Converts `64` to octal without adding any leading zeros.  
   **Result**: `100`

6. **Edge Case with Places**:  
   `=DEC2OCT(255, 2)`  
   When the octal value exceeds the specified `places` length, Excel returns a `#NUM!` error.  
   **Result**: `#NUM!`

### Notes:

- **Range of Input**:  
  The `number` must be between -536,870,912 and 536,870,911. Numbers outside this range trigger a `#NUM!` error.

- **Default `places` Behavior**:  
  If omitted, the function returns the shortest octal representation of the number without any leading zeros.

- **Error Handling**:
    - If `number` is non-numeric, Excel returns a `#VALUE!` error.
    - If `places` is non-numeric or less than 1, Excel also returns a `#VALUE!` error.
    - If the octal result is longer than the specified `places`, Excel returns a `#NUM!` error.

- **Negative Numbers Representation**:  
  Negative numbers are represented in two's complement octal form, meaning they are placed in a signed 30-bit range.

### Applications:

- **Use Cases**:
    - Representing integers in octal for digital systems, file permissions (e.g., in UNIX), or low-level programming.
    - Quickly visualizing octal data directly in spreadsheets for debugging or system design.

- **Complementary Functions**:
    - **OCT2DEC**: Converts an octal number back to a decimal number.
    - **DEC2BIN**: Converts a decimal number to a binary number.
    - **DEC2HEX**: Converts a decimal number to a hexadecimal number.
    - **OCT2BIN**, **OCT2HEX**: Convert octal to other number systems.

### Summary:

The `DEC2OCT` function is a handy tool in Excel for converting decimal numbers into their octal equivalents. Its ability
to handle two's complement and optional zero padding makes it versatile for both basic and advanced use cases in digital
applications.