<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUMSQ Function

The `SUMSQ` function in Excel calculates the sum of the squares of the given numbers or values. It is useful when you
need to work with squared values (e.g., in statistical calculations or mathematical operations).

### Syntax:

    SUMSQ(number1, [number2], ...)

- **number1**: The first number or value to be squared and included in the sum.
- **number2, ...** (optional): Additional numbers, values, or cell ranges to square and include in the sum.

### Key Behaviors:

- Each value is **squared** (multiplied by itself) before being added to the total sum.
- The function accepts numbers, named ranges, or references to ranges that contain numbers.
- Any **non-numeric values** in the input are ignored (treated as zero).
- Logical values (`TRUE`, `FALSE`) are treated as numbers in ranges or arrays:
    - `TRUE` is 1, so `TRUE^2 = 1`.
    - `FALSE` is 0, so `FALSE^2 = 0`.

### Examples:

1. `=SUMSQ(2, 3, 4)`  
   Squares each value and sums the results:  
   \( 2^2 + 3^2 + 4^2 = 4 + 9 + 16 = 29 \)

2. `=SUMSQ(A1:A3)`  
   If `A1:A3` contains `{3, 4, 5}`, the result is:  
   \( 3^2 + 4^2 + 5^2 = 9 + 16 + 25 = 50 \)

3. `=SUMSQ(A1:A3, 6)`  
   If `A1:A3` contains `{1, 2, 3}`, the result is:  
   \( 1^2 + 2^2 + 3^2 + 6^2 = 1 + 4 + 9 + 36 = 50 \)

4. `=SUMSQ({2, TRUE, FALSE})`  
   Squaring each value:  
   \( 2^2 + 1^2 + 0^2 = 4 + 1 + 0 = 5 \)  
   (where `TRUE` acts as `1` and `FALSE` as `0`).

### Usage Notes:

- The `SUMSQ` function is particularly helpful in statistical and mathematical applications, such as calculating *
  *variance** or **quadratic equations**.
- Can be used in combination with other functions to create more complex formulas.
- Ensure inputs are numeric (or ranges with numeric cells) to avoid unexpected results.

> **Tip**: To find the sum of squares for a given data range without manually squaring each value, `SUMSQ` simplifies
the process directly.