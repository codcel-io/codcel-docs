<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BITAND Function

The `BITAND` function in Excel performs a **bitwise AND operation** between two numbers.  
This function is particularly useful in scenarios where bit-level operations are required, such as in computer
science,  
programming, or digital logic design.

### Key Features of BITAND:

- Compares the binary representations of two numbers **bit by bit**.
- Returns a decimal value equivalent to the bitwise AND result.
- Performs the operation as follows:
    - For each bit position, if **both** bits are `1`, the result is `1`; otherwise, the result is `0`.

### Syntax:

```plaintext
BITAND(number1, number2)
```

- **number1**: The first positive number, used as an operand for the bitwise AND operation.
- **number2**: The second positive number, used as another operand for the bitwise AND operation.

### Examples:

1. **Basic Bitwise AND Operation**:  
   `=BITAND(5, 3)`  
   Binary representation of `5` is `101`, and binary of `3` is `011`.  
   Bitwise AND operation produces `001`, which is `1` in decimal.  
   **Result**: `1`

2. **Zero Result from Bitwise AND**:  
   `=BITAND(4, 2)`  
   Binary of `4` is `100`, and binary of `2` is `010`.  
   There's no position where both bits are `1`, so the result is `000`.  
   **Result**: `0`

3. **Larger Numbers**:  
   `=BITAND(14, 11)`  
   Binary of `14` is `1110`, and binary of `11` is `1011`.  
   Performing bitwise AND gives `1010` in binary, which is `10` in decimal.  
   **Result**: `10`

### Notes:

- **Positive Numbers Only**:
    - Both input arguments must be non-negative integers.
    - If any input is not an integer or is negative, Excel will return a `#NUM!` error.

- **Bitwise Logic**:
    - The comparison happens at the **binary level**—each bit is compared independently.
    - The result has the same length as the longest input binary representation.

- **Error Values**:
    - If inputs are not numeric, Excel returns a `#VALUE!` error.
    - If either number is negative or not an integer, Excel returns a `#NUM!` error.

### Applications:

- **Use Case**:
    - The `BITAND` function is commonly used in **digital electronics** and **binary arithmetic** to filter or mask
      specific bits in a number.
    - Useful in scenarios where certain bit-level flags need to be checked.

- **Complementary Functions**:
    - **BITOR**: Performs a bitwise OR operation.
    - **BITXOR**: Performs a bitwise XOR operation.
    - **BITLSHIFT** / **BITRSHIFT**: Shifts bits left or right by a specified number of places.