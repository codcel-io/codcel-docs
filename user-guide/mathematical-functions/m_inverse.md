<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MINVERSE Function

The `MINVERSE` function in Excel calculates the inverse of a square matrix provided as an array or range. The inverse of a matrix \( A \) is a matrix \( B \) such that \( A \times B = I \), where \( I \) is the identity matrix.

### Syntax:

    MINVERSE(array)

- **array**: A square range of cells (e.g., A1:B2) or a 2D array constant that represents a matrix. The number of rows and columns must be equal.

### Examples:

1. **2x2 Matrix**  
   If the range A1:B2 contains:
   ```
   4   7  
   2   6  
   ```  
   Formula: `=MINVERSE(A1:B2)`  
   Returns:
   ```
   0.6   -0.7  
   -0.2   0.4  
   ```
   Explanation: This is the inverse of the 2x2 matrix.

2. **3x3 Matrix**  
   If the range A1:C3 contains:
   ```
   1   2   3  
   0   1   4  
   5   6   0  
   ```  
   Formula: `=MINVERSE(A1:C3)`  
   Returns:
   ```
   -24    18   5  
   20    -15   -4  
   -5     4    1  
   ```
   Explanation: Excel calculates the inverse of the 3x3 matrix.

3. **Single-Cell Matrix**  
   If A1 contains `5`:  
   Formula: `=MINVERSE(A1)`  
   Returns: `0.2`, because the inverse of a 1x1 matrix is \( 1 / \text{value} \).

### Usage Notes:

- The input must be a square matrix; Excel will return a `#VALUE!` error if the rows and columns are not equal.
- If the determinant of the matrix is `0` (i.e., the matrix is singular), Excel will return a `#NUM!` error because the matrix does not have an inverse.
- The `MINVERSE` function must be entered as an **array formula** in versions prior to Excel 365:
    - Select a range with the same dimensions as the original matrix.
    - Enter the formula and press `Ctrl + Shift + Enter`.
- In Excel 365 and Excel 2021, dynamic arrays allow the result to spill automatically without `Ctrl + Shift + Enter`.
- All elements in the input matrix must be numeric; otherwise, Excel will return an error.
- The inverse matrix is widely used in linear algebra to solve systems of linear equations and other mathematical computations.