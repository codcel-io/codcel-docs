<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MMULT Function

The `MMULT` function in Excel returns the matrix product of two arrays. The matrix product is the result of multiplying two matrices, where the number of columns in the first matrix must equal the number of rows in the second matrix.

### Syntax:

    MMULT(array1, array2)

- **array1**: The first matrix (array or range) to multiply.
- **array2**: The second matrix (array or range) to multiply.

The number of columns in `array1` must be equal to the number of rows in `array2`.

### Examples:

1. **Matrix Product of 2x2 Matrices**  
   If the range A1:B2 contains:
   ```
   1   2  
   3   4  
   ```
   and C1:D2 contains:
   ```
   2   0  
   1   3  
   ```
   Formula: `=MMULT(A1:B2, C1:D2)`  
   Returns:
   ```
   4   6  
   10  12  
   ```
   Explanation: Each element is the dot product of the corresponding row and column.

2. **Matrix Product of a 2x3 and a 3x2 Matrix**  
   If A1:C2 contains:
   ```
   1   2   3  
   4   5   6  
   ```
   and D1:E3 contains:
   ```
   7   8  
   9   10  
   11  12  
   ```
   Formula: `=MMULT(A1:C2, D1:E3)`  
   Returns:
   ```
   58   64  
   139  154  
   ```
   Explanation: Excel multiplies rows of the first matrix by columns of the second matrix.

### Usage Notes:

- The number of columns in the first matrix must equal the number of rows in the second matrix; otherwise, Excel will return a `#VALUE!` error.
- The resulting matrix will have dimensions equal to the number of rows in `array1` and the number of columns in `array2`.
- The `MMULT` function must be entered as an **array formula** in versions prior to Excel 365:
    - Select the output range with appropriate dimensions.
    - Enter the formula and press `Ctrl + Shift + Enter`.
- In Excel 365 and Excel 2021, dynamic arrays automatically spill the result.
- All elements in the arrays must be numeric; non-numeric values will result in a `#VALUE!` error.
- `MMULT` is widely used in fields like engineering, statistics, and data analysis for matrix multiplication and linear transformations.