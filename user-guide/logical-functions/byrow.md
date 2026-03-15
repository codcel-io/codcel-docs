<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BYROW Function

The `BYROW` function in Excel allows you to **apply a LAMBDA function to each row** in an array, returning a single-column array of the results. Instead of writing repetitive formulas for each row, you can process every row in a range with a single, readable formula.

BYROW is particularly useful for summarizing or transforming data on a per-row basis, such as calculating row totals, averages, or custom aggregations across a table. It pairs naturally with LAMBDA to create concise, row-wise data processing directly within your formulas.

### Key Features of BYROW:

- Apply a custom LAMBDA function to every row of an array.
- Return a single-column array with one result per row.
- Eliminate the need for repetitive formulas across rows.
- Combine with aggregate functions like SUM, AVERAGE, MAX, and MIN inside the LAMBDA.
- Works with any array or range, regardless of the number of rows or columns.

### Syntax:

```plaintext
BYROW(array, lambda)
```

- **array** (required): The array or range to process row by row.
- **lambda** (required): A LAMBDA function with one parameter that receives each row as an array. The LAMBDA is called once per row and should return a single value.

### How BYROW Works:

The `BYROW` function processes its arguments as follows:

1. Takes an array or range as input.
2. Iterates through each row of the array.
3. Passes the entire row (as a single-row array) to the provided LAMBDA function.
4. Collects each LAMBDA result into a new single-column array.
5. Returns the resulting column array with one element per row.

Each row is processed independently, and the LAMBDA is called once per row.

### Examples:

1. **Sum Each Row**:
   Calculate the total of each row in a range:
   `=BYROW(A1:C5, LAMBDA(row, SUM(row)))`
   The BYROW passes each row to the LAMBDA, which sums it.
   **Result**: A single-column array with the sum of each row (e.g., if rows total 10, 20, 30, 40, 50, the result is {10; 20; 30; 40; 50}).

2. **Average Each Row**:
   Find the average of each row:
   `=BYROW(A1:D10, LAMBDA(row, AVERAGE(row)))`
   The BYROW calculates the average for each row independently.
   **Result**: A single-column array of row averages.

3. **Find the Maximum in Each Row**:
   Get the highest value from each row:
   `=BYROW(A1:C5, LAMBDA(row, MAX(row)))`
   The BYROW finds the maximum value in each row.
   **Result**: A single-column array of row maximums (e.g., {100; 85; 92; 78; 95}).

4. **Count Non-Empty Cells in Each Row**:
   Count how many cells contain data in each row:
   `=BYROW(A1:E10, LAMBDA(row, COUNTA(row)))`
   The BYROW counts non-empty cells per row.
   **Result**: A single-column array of counts for each row.

5. **Apply Conditional Aggregation**:
   Count values greater than 50 in each row:
   `=BYROW(A1:C10, LAMBDA(row, SUMPRODUCT((row > 50) * 1)))`
   The BYROW applies a conditional count to each row.
   **Result**: A single-column array with the count of values above 50 per row.

6. **Calculate Standard Deviation per Row**:
   Compute the standard deviation for each row:
   `=BYROW(A1:D20, LAMBDA(row, STDEV(row)))`
   The BYROW calculates the spread of values in each row.
   **Result**: A single-column array of standard deviations.

7. **Combine BYROW with LET**:
   Use LET inside the LAMBDA for clarity:
   `=BYROW(A1:C10, LAMBDA(row, LET(avg, AVERAGE(row), mx, MAX(row), mx - avg)))`
   The BYROW calculates the difference between the max and average for each row.
   **Result**: A single-column array showing how far the max is above the average in each row.

### Notes:

- `BYROW` is available in Excel 365 and Excel 2024 or later versions.
- The LAMBDA must accept exactly one parameter, which receives each row as an array.
- The LAMBDA should return a single value for each row; if it returns an array, BYROW returns a `#VALUE!` error.
- If the LAMBDA returns an error for any row, that element in the result array will contain the error.
- BYROW processes rows from top to bottom.
- BYROW can be combined with other dynamic array functions like FILTER, SORT, and UNIQUE for powerful data transformations.

### Related Functions:

- **BYCOL**: Applies a LAMBDA function to each column of an array, returning a single-row array.
  Example: `=BYCOL(A1:C5, LAMBDA(col, SUM(col)))` sums each column.

- **MAP**: Applies a LAMBDA function to each individual element in an array.
  Example: `=MAP(A1:A5, LAMBDA(x, x * 2))` doubles each value.

- **LAMBDA**: Creates custom, reusable functions with user-defined parameters.
  Example: `=LAMBDA(x, x * 2)(5)` returns `10`.

- **REDUCE**: Reduces an array to a single value by applying a LAMBDA cumulatively.
  Example: `=REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x))` sums the values.

### Summary:

The `BYROW` function is a powerful tool for processing arrays on a row-by-row basis by applying a LAMBDA function to each row. It eliminates the need for repetitive row-specific formulas, making row-wise aggregations and transformations concise and readable. Whether you need to sum rows, find row maximums, count values, or perform custom calculations across each row of a dataset, BYROW provides a clean, functional approach to row-wise array processing.