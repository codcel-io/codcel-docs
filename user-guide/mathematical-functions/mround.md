<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MROUND Function

The `MROUND` function in Excel rounds a number to the nearest multiple of a specified value.

### Syntax:

    MROUND(number, multiple)

- **number**: The value to be rounded.
- **multiple**: The multiple to which you want to round the number.

The function rounds the value up or down, depending on which multiple is closer.

### Examples:

1. **Round to the nearest 5**  
   Formula: `=MROUND(12, 5)`  
   Returns: `10`  
   Explanation: 10 is the closest multiple of 5 to 12.

2. **Round to the nearest 10**  
   Formula: `=MROUND(27, 10)`  
   Returns: `30`  
   Explanation: 30 is the nearest multiple of 10 to 27.

3. **Round a negative number**  
   Formula: `=MROUND(-13, -4)`  
   Returns: `-12`  
   Explanation: -12 is the closest multiple of -4 to -13.

4. **Round with decimals**  
   Formula: `=MROUND(7.3, 0.5)`  
   Returns: `7.5`  
   Explanation: 7.5 is the closest multiple of 0.5 to 7.3.

### Usage Notes:

- The `MROUND` function requires both the **number** and **multiple** to have the same sign; otherwise, it will return a `#NUM!` error.
- If the number is equidistant between two multiples, the function rounds **away from zero**.
- `MROUND` is commonly used in financial and engineering calculations to round numbers to desired intervals, such as 5, 10, or specific decimal increments.