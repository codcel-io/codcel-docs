<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BITLSHIFT Function

The `BITLSHIFT` function in Excel performs a **bitwise left shift** on a given number.  
This operation shifts the bits of the binary representation of a number to the left by a specified number of
positions,  
with zeros filling in from the right. The function is commonly used in computing scenarios such as binary arithmetic,  
power-of-two calculations, and digital logic design.

### Key Features of BITLSHIFT:

- Shifts the bits in a number to the **left** by a specified number of places.
- Each left shift effectively multiplies the number by `2^shift_amount`.
- Returns the decimal equivalent of the resulting binary number after the shift.

### Syntax:

```plaintext
BITLSHIFT(number, shift_amount)
```

- **number**: The decimal number to be shifted. This must be a positive integer.
- **shift_amount**: The number of bits to shift to the left.
    - Must be greater than or equal to 0.
    - If `shift_amount` is negative, Excel will return a `#NUM!` error.

### Examples:

1. **Basic Left Shift**:  
   `=BITLSHIFT(5, 2)`  
   Binary representation of `5` is `101`. Shifting left by 2 positions gives `10100`, which is `20` in decimal.  
   **Result**: `20`

2. **No Shift**:  
   `=BITLSHIFT(8, 0)`  
   Binary representation of `8` is `1000`. Left shift by 0 positions results in no change.  
   **Result**: `8`

3. **Large Shift**:  
   `=BITLSHIFT(3, 3)`  
   Binary representation of `3` is `11`. Shifting left by 3 positions gives `11000`, which is `24` in decimal.  
   **Result**: `24`

4. **Error Due to Negative Shift**:  
   `=BITLSHIFT(4, -2)`  
   Negative shift values are not allowed, so Excel will return `#NUM!`.

### Notes:

- **Integer Inputs Only**:
    - Both `number` and `shift_amount` must be non-negative integers.
    - If either input is a fraction or negative, Excel returns a `#NUM!` error.

- **Bitwise Logic**:
    - Every left shift corresponds to multiplying the number by a power of two:  
      `Result = number * (2^shift_amount)`.

- **Zero Behavior**:
    - If `number` is `0`, the result will always be `0`, regardless of the `shift_amount`.

- **Error Handling**:
    - If inputs are not numeric, Excel will return a `#VALUE!` error.
    - If `number` or `shift_amount` are negative, Excel will return a `#NUM!` error.

### Applications:

- **Use Case**:
    - The `BITLSHIFT` function is particularly useful in scenarios where power-of-two multiplications are required.
    - Commonly used in low-level bit manipulation, **binary masking**, or **encoding data** in digital logic.

- **Complementary Functions**:
    - **BITAND**: Performs a bitwise AND operation.
    - **BITOR**: Performs a bitwise OR operation.
    - **BITRSHIFT**: Shifts bits to the right by a specified number of places.
    - **BITXOR**: Performs a bitwise XOR operation.