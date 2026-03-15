<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BYCOL Function

The `BYCOL` function in Excel allows you to **apply a LAMBDA function to each column** in an array, returning a single-row array of the results. Instead of writing repetitive formulas for each column, you can process every column in a range with a single, readable formula.

BYCOL is particularly useful for summarizing or transforming data on a per-column basis, such as calculating column totals, averages, or custom aggregations across a table. It pairs naturally with LAMBDA to create concise, column-wise data processing directly within your formulas.

### Key Features of BYCOL:

- Apply a custom LAMBDA function to every column of an array.
- Return a single-row array with one result per column.
- Eliminate the need for repetitive formulas across columns.
- Combine with aggregate functions like SUM, AVERAGE, MAX, and MIN inside the LAMBDA.
- Works with any array or range, regardless of the number of rows or columns.

### Syntax:

```plaintext
BYCOL(array, lambda)
```

- **array** (required): The array or range to process column by column.
- **lambda** (required): A LAMBDA function with one parameter that receives each column as an array. The LAMBDA is called once per column and should return a single value.

### How BYCOL Works:

The `BYCOL` function processes its arguments as follows:

1. Takes an array or range as input.
2. Iterates through each column of the array.
3. Passes the entire column (as a single-column array) to the provided LAMBDA function.
4. Collects each LAMBDA result into a new single-row array.
5. Returns the resulting row array with one element per column.

Each column is processed independently, and the LAMBDA is called once per column.

### Examples:

1. **Sum Each Column**:
   Calculate the total of each column in a range:
   `=BYCOL(A1:C5, LAMBDA(col, SUM(col)))`
   The BYCOL passes each column to the LAMBDA, which sums it.
   **Result**: A single-row array with the sum of each column (e.g., if columns total 10, 20, 30, the result is {10, 20, 30}).

2. **Average Each Column**:
   Find the average of each column:
   `=BYCOL(A1:D10, LAMBDA(col, AVERAGE(col)))`
   The BYCOL calculates the average for each column independently.
   **Result**: A single-row array of column averages.

3. **Find the Maximum in Each Column**:
   Get the highest value from each column:
   `=BYCOL(A1:C5, LAMBDA(col, MAX(col)))`
   The BYCOL finds the maximum value in each column.
   **Result**: A single-row array of column maximums (e.g., {100, 85, 92}).

4. **Count Non-Empty Cells in Each Column**:
   Count how many cells contain data in each column:
   `=BYCOL(A1:E10, LAMBDA(col, COUNTA(col)))`
   The BYCOL counts non-empty cells per column.
   **Result**: A single-row array of counts for each column.

5. **Apply Conditional Aggregation**:
   Count values greater than 50 in each column:
   `=BYCOL(A1:C10, LAMBDA(col, SUMPRODUCT((col > 50) * 1)))`
   The BYCOL applies a conditional count to each column.
   **Result**: A single-row array with the count of values above 50 per column.

6. **Calculate Standard Deviation per Column**:
   Compute the standard deviation for each column:
   `=BYCOL(A1:D20, LAMBDA(col, STDEV(col)))`
   The BYCOL calculates the spread of values in each column.
   **Result**: A single-row array of standard deviations.

7. **Combine BYCOL with LET**:
   Use LET inside the LAMBDA for clarity:
   `=BYCOL(A1:C10, LAMBDA(col, LET(avg, AVERAGE(col), mx, MAX(col), mx - avg)))`
   The BYCOL calculates the difference between the max and average for each column.
   **Result**: A single-row array showing how far the max is above the average in each column.

### Notes:

- `BYCOL` is available in Excel 365 and Excel 2024 or later versions.
- The LAMBDA must accept exactly one parameter, which receives each column as an array.
- The LAMBDA should return a single value for each column; if it returns an array, BYCOL returns a `#VALUE!` error.
- If the LAMBDA returns an error for any column, that element in the result array will contain the error.
- BYCOL processes columns from left to right.
- BYCOL can be combined with other dynamic array functions like FILTER, SORT, and UNIQUE for powerful data transformations.

### Related Functions:

- **BYROW**: Applies a LAMBDA function to each row of an array, returning a single-column array.
  Example: `=BYROW(A1:C5, LAMBDA(row, SUM(row)))` sums each row.

- **MAP**: Applies a LAMBDA function to each individual element in an array.
  Example: `=MAP(A1:A5, LAMBDA(x, x * 2))` doubles each value.

- **LAMBDA**: Creates custom, reusable functions with user-defined parameters.
  Example: `=LAMBDA(x, x * 2)(5)` returns `10`.

- **REDUCE**: Reduces an array to a single value by applying a LAMBDA cumulatively.
  Example: `=REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x))` sums the values.

### Summary:

The `BYCOL` function is a powerful tool for processing arrays on a column-by-column basis by applying a LAMBDA function to each column. It eliminates the need for repetitive column-specific formulas, making column-wise aggregations and transformations concise and readable. Whether you need to sum columns, find column maximums, count values, or perform custom calculations across each column of a dataset, BYCOL provides a clean, functional approach to column-wise array processing.