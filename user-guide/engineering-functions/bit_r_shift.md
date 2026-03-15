<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BITRSHIFT Function

The `BITRSHIFT` function in Excel performs a **bitwise right shift** operation on a given number by shifting its binary
representation to the right by a specified number of bits. For each shift, the least significant bit (rightmost bit) is
removed, and a `0` is added to the most significant bit (leftmost position). This operation effectively divides the
number by `2^n`, where `n` is the number of places to shift, discarding any remainder.

### Key Features of BITRSHIFT:

- Shifts the binary representation of a number to the right by a specified number of bits.
- The result is equivalent to integer division by `2^n`.
- Useful for low-level programming, binary arithmetic, and data manipulation tasks.

### Syntax:

```plaintext
BITRSHIFT(number, shift_amount)
```

- **number**: The non-negative integer to be shifted.
- **shift_amount**: The number of bit positions to shift:
    - Must be an integer.
    - A positive `shift_amount` shifts bits to the right.
    - A negative `shift_amount` shifts bits to the left (essentially behaving like `BITLSHIFT`).

### Examples:

1. **Basic Right Shift**:  
   `=BITRSHIFT(8, 1)`  
   Binary representation of `8` is `1000`. Shifting right by 1 bit gives `0100` (4 in decimal).  
   **Result**: `4`

2. **Right Shift by Two Bits**:  
   `=BITRSHIFT(16, 2)`  
   Binary representation of `16` is `10000`. Shifting right by 2 bits gives `00100` (4 in decimal).  
   **Result**: `4`

3. **Shift Beyond Number of Bits**:  
   `=BITRSHIFT(5, 4)`  
   Binary representation of `5` is `101`. Shifting right by 4 bits removes all bits, leaving only `0`.  
   **Result**: `0`

4. **Negative Shift Amount**:  
   `=BITRSHIFT(3, -2)`  
   A negative shift amount results in a left shift of 2 bits. Binary `11` becomes `1100` (12 in decimal).  
   **Result**: `12`

5. **Error with Negative Number**:  
   `=BITRSHIFT(-3, 2)`  
   Negative numbers are not valid for the `number` argument, so Excel returns a `#NUM!` error.  
   **Result**: `#NUM!`

### Notes:

- **Non-Negative Numbers Only**:
    - The `number` argument must be a non-negative integer. A negative input results in a `#NUM!` error.

- **Shifting by Zero**:
    - If `shift_amount` is `0`, the result is the same as the input `number`.

- **Right Shift Behavior**:
    - For each bit shifted right, the number is divided by `2`.
    - Bits that are shifted out of the rightmost position are discarded; zeros fill in from the left.

- **Error Handling**:
    - If `number` is not an integer or is negative, Excel returns a `#NUM!` error.
    - If `shift_amount` is not an integer, Excel returns a `#VALUE!` error.

### Applications:

- **Use Case**:
    - The `BITRSHIFT` function is useful for performing quick integer division by powers of 2.
    - Commonly used in bit-level data manipulation, flag encoding/decoding, and binary protocols.

- **Complementary Functions**:
    - **BITLSHIFT**: Shifts bits to the left by a specified number of places.
    - **BITAND**: Performs a bitwise AND operation.
    - **BITOR**: Performs a bitwise OR operation.
    - **BITXOR**: Performs a bitwise XOR operation.