<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BITXOR Function

The `BITXOR` function in Excel performs a **bitwise XOR (exclusive OR)** operation between the binary representations of
two numbers. The XOR operation compares each bit in the binary forms of the two numbers, and the result is `1` if the
bits are different and `0` if the bits are the same.

In simpler terms:

- If a bit in one number is `1` and the corresponding bit in the other is `0`, the result bit will be `1`.
- If both corresponding bits are the same (both `1` or both `0`), the result bit will be `0`.

### Key Features of BITXOR:

- Outputs the binary XOR operation between two integers.
- The result combines binary values from two numbers where differences in their bits determine `1`, and similarities
  determine `0`.
- Useful for cryptography, binary logic, and low-level data manipulation.

### Syntax:

```plaintext
BITXOR(number1, number2)
```

- **number1**: A non-negative integer.
- **number2**: A non-negative integer.

### Examples:

1. **Basic XOR Operation**:  
   `=BITXOR(5, 3)`  
   Binary representation of `5` is `0101`, and `3` is `0011`.  
   XOR operation:
   ```
   0101
   0011
   ----
   0110
   ```
   Binary `0110` is `6` in decimal.  
   **Result**: `6`

2. **XOR with Zero**:  
   `=BITXOR(7, 0)`  
   Binary representation of `7` is `0111`. XOR with zero leaves the number unchanged.  
   **Result**: `7`

3. **XOR of Same Numbers**:  
   `=BITXOR(9, 9)`  
   Binary representation of `9` is `1001`. XOR of any number with itself results in `0` because every bit is the same.  
   **Result**: `0`

4. **XOR with Larger Numbers**:  
   `=BITXOR(15, 6)`  
   Binary representation of `15` is `1111`, and `6` is `0110`.  
   XOR operation:
   ```
   1111
   0110
   ----
   1001
   ```
   Binary `1001` is `9` in decimal.  
   **Result**: `9`

### Notes:

- **Non-Negative Numbers Only**:
    - The inputs `number1` and `number2` must be non-negative integers. Negative inputs will result in a `#NUM!` error.

- **Error for Non-Integers**:
    - If either `number1` or `number2` is not an integer, Excel returns a `#VALUE!` error.

- **Behavior with XOR**:
    - XOR always clears (results in `0`) when both bits are the same.
    - XOR is commutative: `BITXOR(a, b)` equals `BITXOR(b, a)`.

### Applications:

- **Use Case**:
    - Useful for toggling bits or performing simple cryptographic operations.
    - Ensures differentiation between changes in binary data.

- **Complementary Functions**:
    - **BITAND**: Performs a bitwise AND operation.
    - **BITOR**: Performs a bitwise OR operation.
    - **BITLSHIFT**: Shifts bits to the left by a specified number.
    - **BITRSHIFT**: Shifts bits to the right by a specified number.