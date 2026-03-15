<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DEC2BIN Function

The `DEC2BIN` function in Excel converts a decimal number (base 10) into a binary number (base 2) in text format.

### Key Features of DEC2BIN:

- Converts a decimal number into its binary representation.
- Handles both positive and negative decimal numbers.
- Frequently used in digital systems, computer science, and electronics to represent numbers in binary notation.

### Syntax:

```plaintext
DEC2BIN(number, [places])
```

- **number**: The decimal number to be converted to binary. Must be an integer between -512 and 511.
- **places** (optional): The number of characters to pad the binary number with. Adds leading zeros to ensure the result
  has the specified total length.

### Examples:

1. **Basic Conversion**:  
   `=DEC2BIN(10)`  
   Converts the decimal number `10` to binary.  
   **Result**: `1010`

2. **Specifying Places**:  
   `=DEC2BIN(10, 6)`  
   Converts the decimal `10` to binary and pads it to six places with leading zeros.  
   **Result**: `001010`

3. **Negative Number Conversion**:  
   `=DEC2BIN(-5)`  
   Converts the decimal `-5` to binary using two's complement.  
   **Result**: `11111011`

4. **Zero Padding for Large Positive Numbers**:  
   `=DEC2BIN(7, 5)`  
   Converts the decimal `7` to `0111` and pads it to five places.  
   **Result**: `000111`

5. **Omitting Places**:  
   `=DEC2BIN(20)`  
   Converts the decimal `20` to binary without additional padding.  
   **Result**: `10100`

### Notes:

- **Range of Input**:  
  The `number` must be within the range of -512 to 511. Any number outside this range returns the `#NUM!` error.

- **Default `places` Behavior**:  
  If omitted, the result will not include padding and will simply return the shortest binary representation of the
  number.

- **Error Handling**:
    - If the `number` parameter is non-numeric, Excel returns a `#VALUE!` error.
    - If the `places` parameter is non-numeric or zero, Excel also returns a `#VALUE!` error.
    - If the binary result exceeds the length specified by `places`, Excel returns a `#NUM!` error.

- **Negative Numbers Representation**:  
  For negative numbers, the binary result is calculated in two's complement form, ensuring the value can be used in
  signed binary calculations.

### Applications:

- **Use Cases**:
    - Representing decimal values in binary for digital systems, electronics, and programming.
    - Pre-processing binary values for use in logical or mathematical operations.
    - Converting negative numbers into two's complement binary.

- **Complementary Functions**:
    - **BIN2DEC**: Converts a binary number back to a decimal number.
    - **DEC2HEX**: Converts a decimal number to a hexadecimal number.
    - **DEC2OCT**: Converts a decimal number to an octal number.
    - **BIN2HEX**, **BIN2OCT**: Convert binary to other number systems.

### Summary:

The `DEC2BIN` function is a useful tool in Excel for converting decimal numbers to binary, making it essential for
numerical and computational applications. It simplifies the process of representing and manipulating binary data,
especially for engineers, programmers, and mathematicians.