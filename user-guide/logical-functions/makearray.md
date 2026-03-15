<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MAKEARRAY Function

The `MAKEARRAY` function in Excel allows you to **create an array of a specified size** by applying a LAMBDA function to generate each element. Instead of manually building tables or using complex nested formulas, you can dynamically construct arrays where each cell's value is determined by its row and column position.

MAKEARRAY is particularly useful for generating multiplication tables, matrices, grids of computed values, and any structured data that follows a pattern based on row and column indices. It pairs naturally with LAMBDA to produce custom arrays directly within your formulas.

### Key Features of MAKEARRAY:

- Create arrays of any specified row and column dimensions.
- Generate each element dynamically using a LAMBDA function that receives the row and column index.
- Eliminate the need for helper ranges when building computed tables or matrices.
- Combine with other functions like IF, MOD, and mathematical operations inside the LAMBDA for complex patterns.
- Row and column indices passed to the LAMBDA are 1-based (starting from 1, not 0).

### Syntax:

```plaintext
MAKEARRAY(rows, cols, lambda)
```

- **rows** (required): The number of rows in the resulting array. Must be a positive integer.
- **cols** (required): The number of columns in the resulting array. Must be a positive integer.
- **lambda** (required): A LAMBDA function with two parameters (row index and column index) that returns the value for each element in the array.

### How MAKEARRAY Works:

The `MAKEARRAY` function processes its arguments as follows:

1. Creates an empty array with the specified number of rows and columns.
2. Iterates through each position in the array, from top-left to bottom-right.
3. Passes the current row index and column index (both 1-based) to the LAMBDA function.
4. Places the LAMBDA's return value into the corresponding position in the array.
5. Returns the completed array.

Each element is generated independently based on its row and column position.

### Examples:

1. **Create a Multiplication Table**:
   Generate a 5x5 multiplication table:
   `=MAKEARRAY(5, 5, LAMBDA(r, c, r * c))`
   The MAKEARRAY creates a 5-row, 5-column array where each cell is the product of its row and column number.
   **Result**: A 5x5 grid (e.g., row 3, column 4 = 12).

2. **Generate a Constant Array**:
   Fill every cell with the same value:
   `=MAKEARRAY(3, 4, LAMBDA(r, c, 0))`
   The MAKEARRAY creates a 3x4 array filled with zeros.
   **Result**: A 3x4 grid of zeros.

3. **Build an Identity Matrix**:
   Create a matrix with 1s on the diagonal and 0s elsewhere:
   `=MAKEARRAY(4, 4, LAMBDA(r, c, IF(r = c, 1, 0)))`
   The MAKEARRAY checks if the row and column indices match to place 1s on the diagonal.
   **Result**: A 4x4 identity matrix.

4. **Create a Sequential Number Grid**:
   Generate sequential numbers across rows:
   `=MAKEARRAY(3, 5, LAMBDA(r, c, (r - 1) * 5 + c))`
   The MAKEARRAY calculates a sequential number based on position.
   **Result**: A 3x5 grid with values 1 through 15.

5. **Generate a Checkerboard Pattern**:
   Alternate between two values based on position:
   `=MAKEARRAY(4, 4, LAMBDA(r, c, IF(MOD(r + c, 2) = 0, "X", "O")))`
   The MAKEARRAY uses MOD to alternate values in a checkerboard pattern.
   **Result**: A 4x4 grid alternating "X" and "O".

6. **Create a Triangular Matrix**:
   Fill the lower triangle with values and the upper triangle with zeros:
   `=MAKEARRAY(4, 4, LAMBDA(r, c, IF(r >= c, r + c, 0)))`
   The MAKEARRAY places computed values only where the row index is greater than or equal to the column index.
   **Result**: A 4x4 lower-triangular matrix.

7. **Combine MAKEARRAY with LET**:
   Use LET inside the LAMBDA for clearer logic:
   `=MAKEARRAY(3, 3, LAMBDA(r, c, LET(sum, r + c, IF(sum > 4, "High", "Low"))))`
   The MAKEARRAY classifies each position based on the sum of its indices.
   **Result**: A 3x3 grid of "High" or "Low" labels.

### Notes:

- `MAKEARRAY` is available in Excel 365 and Excel 2024 or later versions.
- The `rows` and `cols` arguments must be positive integers; otherwise, MAKEARRAY returns a `#VALUE!` error.
- The LAMBDA must accept exactly two parameters (row index and column index).
- Row and column indices are 1-based: the top-left element receives row = 1, column = 1.
- If the LAMBDA returns an error for any position, that element in the result array will contain the error.
- MAKEARRAY can be combined with other dynamic array functions like MAP, REDUCE, and SCAN for advanced data generation.

### Related Functions:

- **LAMBDA**: Creates custom, reusable functions with user-defined parameters.
  Example: `=LAMBDA(x, x * 2)(5)` returns `10`.

- **MAP**: Applies a LAMBDA function to each element in an array, returning a new array.
  Example: `=MAP(A1:A5, LAMBDA(x, x * 2))` doubles each value.

- **LET**: Assigns names to calculation results within a formula, reducing repetition.
  Example: `=LET(x, 10, y, 20, x + y)` returns `30`.

- **SEQUENCE**: Generates a list of sequential numbers in an array.
  Example: `=SEQUENCE(5, 3, 1, 1)` creates a 5x3 array of sequential numbers starting at 1.

### Summary:

The `MAKEARRAY` function is a powerful tool for dynamically generating arrays of any size by applying a LAMBDA function to each row and column position. It eliminates the need for helper ranges and complex nested formulas when building computed tables, matrices, or patterned grids. Whether you need multiplication tables, identity matrices, sequential grids, or custom patterns, MAKEARRAY provides a clean, functional approach to array construction.