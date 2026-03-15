<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ODD Function

The `ODD` function in Excel rounds a given number **up** to the nearest odd integer. If the number is already an odd integer, no rounding occurs. This function is useful when you need to ensure odd-numbered outputs in calculations.

### Syntax:

```
ODD(number)
```

- **number**: The numeric value you want to round up to the nearest odd integer. It can be positive or negative.

### Examples:

1. `=ODD(2.3)`
   Returns:
   ```
   3
   ```
   Explanation: `2.3` is rounded up to the nearest odd integer `3`.

2. `=ODD(4)`
   Returns:
   ```
   5
   ```
   Explanation: `4` is rounded up to the nearest odd integer `5`.

3. `=ODD(-2.7)`
   Returns:
   ```
   -3
   ```
   Explanation: `-2.7` is rounded up (toward zero for negative numbers) to the nearest odd integer `-3`.

4. `=ODD(7)`
   Returns:
   ```
   7
   ```
   Explanation: Since `7` is already an odd integer, no rounding is needed.

### Usage Notes:

- The `ODD` function always rounds **away from zero** for positive numbers and **toward zero** for negative numbers.
- If the input is non-numeric, Excel returns a `#VALUE!` error.
- Zero (`0`) is treated as positive, so `=ODD(0)` returns `1`.
- This function is particularly helpful in scenarios where odd-numbered values are required, such as in row counts, allocation of items, or grid alignments.

### Example Use Case:
Suppose you are designing a seating arrangement where rows must have an odd number of seats. Using the `ODD` function ensures the count of seats meets this requirement even when input values fluctuate.