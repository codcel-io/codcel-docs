<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUMPRODUCT Function

The `SUMPRODUCT` function in Excel multiplies corresponding elements in arrays and returns the sum of those products. It
is a versatile function commonly used for weighted sums, conditional calculations, and more.

### Syntax:

    SUMPRODUCT(array1, [array2], ...)

- **array1**: The first array or range of cells whose corresponding elements will be multiplied.
- **array2, ...** (optional): Additional arrays or ranges to multiply with `array1`. The function can handle multiple
  arrays.

### Key Behaviors:

- If only one array is provided, `SUMPRODUCT` will simply sum all the values in that array.
- If multiple arrays are provided, the function multiplies corresponding elements in all arrays and sums up the results.
- Arrays/ ranges must have the **same shape (number of rows and columns)**. Otherwise, Excel will return a `#VALUE!`
  error.

### Examples:

1. `=SUMPRODUCT(A1:A5, B1:B5)`  
   Multiplies each pair of corresponding cells in `A1:A5` and `B1:B5`, then sums the results.  
   Example: If `A1:A5` contains `{1, 2, 3, 4, 5}` and `B1:B5` contains `{2, 4, 6, 8, 10}`, the result is  
   `(1×2) + (2×4) + (3×6) + (4×8) + (5×10) = 110`.

2. `=SUMPRODUCT((A1:A5>50)*B1:B5)`  
   Multiplies values in `B1:B5` only where the values in `A1:A5` are greater than 50.  
   Example: If `A1:A5` contains `{30, 60, 70, 40, 80}` and `B1:B5` contains `{10, 20, 30, 40, 50}`, the result is  
   `0×10 + 1×20 + 1×30 + 0×40 + 1×50 = 100`.

3. `=SUMPRODUCT(A1:A5, B1:B5, C1:C5)`  
   Multiplies corresponding elements in three arrays and sums the results.  
   Example: If `A1:A5 = {1, 2, 3, 4, 5}`, `B1:B5 = {1, 1, 1, 1, 1}`, and `C1:C5 = {10, 20, 30, 40, 50}`, the result is  
   `(1×1×10) + (2×1×20) + (3×1×30) + (4×1×40) + (5×1×50) = 550`.

### Usage Notes:

- `SUMPRODUCT` is often used as an alternative to `ARRAYFORMULA` or other array functions in scenarios involving
  conditional multiplication.
- **Logical Conditions**: To multiply based on conditions, you can combine a logical expression with the multiplication
  operation (e.g., `(range>condition)*other_range`).
    - Logical conditions return an array of `TRUE` (1) and `FALSE` (0), allowing conditional calculations.
- Non-numeric values in the arrays will be treated as zeros during calculations.
- You can use `SUMPRODUCT` for tasks like weighted averages or multi-criteria summing without needing to enter array
  formulas (`Ctrl+Shift+Enter`).

> **Note**: Double-check array dimensions to avoid errors and ensure accurate calculations.