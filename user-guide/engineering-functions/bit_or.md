<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BITOR Function

The `BITOR` function in Excel performs a **bitwise OR** operation between two numbers.  
A bitwise OR compares each bit in the binary representation of two numbers, and the result will have a  
bit set to `1` if at least one of the corresponding bits from either number is `1`. The function is  
commonly used in binary operations, bit masking, and low-level programming tasks.

### Key Features of BITOR:

- Performs a **bitwise OR** operation between two decimal numbers.
- Compares the binary representation of the numbers bit by bit.
- Returns a decimal result based on the OR operation performed.

### Syntax:

```plaintext
BITOR(number1, number2)
```

- **number1**: The first non-negative integer.
- **number2**: The second non-negative integer.
    - Both inputs must be integers greater than or equal to `0`.
    - If either number is not an integer or is negative, Excel will return a `#NUM!` error.

### Examples:

1. **Basic OR Operation**:  
   `=BITOR(5, 3)`  
   Binary representation of `5` is `101`, and `3` is `011`.  
   Performing OR gives `111`, which is `7` in decimal.  
   **Result**: `7`

2. **OR Zero**:  
   `=BITOR(6, 0)`  
   Binary representation of `6` is `110`, and `0` is `000`.  
   Performing OR gives `110`, which is `6` in decimal.  
   **Result**: `6`

3. **OR with Itself**:  
   `=BITOR(8, 8)`  
   Binary representation of `8` is `1000`. Performing OR with itself results in no change.  
   **Result**: `8`

4. **Error with Negative Input**:  
   `=BITOR(5, -1)`  
   Negative inputs are not allowed, so Excel will return a `#NUM!` error.

### Notes:

- **Integer Inputs Only**:
    - Both `number1` and `number2` must be non-negative integers.
    - If either input is a fraction or negative, Excel returns a `#NUM!` error.

- **Bitwise Logic**:
    - The result of each bit will be `1` if at least one of the corresponding bits is `1`.

- **Zero Behavior**:
    - If either input is `0`, the result will be the value of the other number.

- **Error Handling**:
    - If inputs are not numeric, Excel will return a `#VALUE!` error.
    - If `number1` or `number2` are negative, Excel will return a `#NUM!` error.

### Applications:

- **Use Case**:
    - The `BITOR` function is particularly useful for setting specific bits in binary masks.
    - Commonly used in digital logic, binary encoding, and flag-based programming.

- **Complementary Functions**:
    - **BITAND**: Performs a bitwise AND operation.
    - **BITLSHIFT**: Shifts bits to the left by a specified number of places.
    - **BITRSHIFT**: Shifts bits to the right.
    - **BITXOR**: Performs a bitwise XOR operation.