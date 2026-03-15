<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->


## MDETERM Function

The `MDETERM` function in Excel calculates the determinant of a square matrix provided as an array or range. Determinants are used in linear algebra to solve systems of equations, calculate inverse matrices, and more.

### Syntax:

    MDETERM(array)

- **array**: A square range of cells (e.g., A1:B2) or a 2D array constant that represents a matrix. The number of rows and columns must be equal.

### Examples:

1. **2x2 Matrix**  
   If the range A1:B2 contains:
   ```
   2   3  
   4   5  
   ```  
   Formula: `=MDETERM(A1:B2)`  
   Returns: `-2`, because the determinant of the matrix is calculated as:  
   \( (2 \times 5) - (3 \times 4) = -2 \).

2. **3x3 Matrix**  
   If the range A1:C3 contains:
   ```
   1   2   3  
   4   5   6  
   7   8   9  
   ```  
   Formula: `=MDETERM(A1:C3)`  
   Returns: `0`, because the determinant of this matrix is zero.

3. **Single-Cell Matrix**  
   Formula: `=MDETERM(A1)` where A1 contains `7`  
   Returns: `7`, because the determinant of a 1x1 matrix is the value of the single element.

### Usage Notes:

- The input must be a square matrix; if the number of rows and columns are not equal, Excel will return a `#VALUE!` error.
- Ensure all the cells in the range contain numeric values; non-numeric values will result in an error.
- The `MDETERM` function is particularly useful in fields like engineering, physics, and economics where matrix calculations are common.
- Determinants are often used to determine if a matrix is invertible (a matrix with a determinant of 0 is not invertible).