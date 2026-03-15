<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SCAN Function

The `SCAN` function in Excel allows you to **apply a LAMBDA function cumulatively to each element** of an array, returning an array of intermediate accumulated values. Like REDUCE, it processes elements in order with an accumulator — but instead of returning only the final result, SCAN returns every intermediate accumulator value as an array.

SCAN is particularly useful for building running totals, cumulative products, progressive text concatenations, and any scenario where you need to see the step-by-step evolution of an accumulation. It pairs naturally with LAMBDA to express iterative logic directly within a single formula, without helper columns or VBA.

### Key Features of SCAN:

- Apply a LAMBDA function cumulatively to each element of an array, returning all intermediate results.
- Start from a user-defined initial value that acts as the accumulator's seed.
- Access both the running accumulator and the current element in each step.
- Return an array with the same dimensions as the input, where each element is the accumulator after processing that step.
- Combine with other functions like IF, LET, and TEXT inside the LAMBDA for complex cumulative patterns.

### Syntax:

```plaintext
SCAN(initial_value, array, lambda)
```

- **initial_value** (required): The starting value for the accumulator. This is the value passed to the LAMBDA on the first iteration before any array elements are processed.
- **array** (required): The array or range to scan over. Elements are processed in row-major order (left to right, top to bottom).
- **lambda** (required): A LAMBDA function with exactly two parameters. The first parameter receives the current accumulator value and the second receives the current array element. The LAMBDA must return the updated accumulator value.

### How SCAN Works:

The `SCAN` function processes its arguments as follows:

1. Sets the accumulator to the provided `initial_value`.
2. Takes the first element of the array and calls the LAMBDA with the accumulator and that element.
3. The LAMBDA's return value becomes the new accumulator and is stored as the first element of the result array.
4. Repeats for each subsequent element, passing the updated accumulator and the next element, storing each new accumulator value.
5. After all elements have been processed, returns the full array of accumulated values.

Each element is processed in order, and the result array shows the accumulator's value after each step.

### Examples:

1. **Running Total (Cumulative Sum)**:
   Build a running sum across a range:
   `=SCAN(0, A1:A5, LAMBDA(acc, x, acc + x))`
   The SCAN starts at 0 and adds each value, returning all intermediate sums.
   **Result**: An array of cumulative sums (e.g., if A1:A5 is {10,20,30,40,50}, the result is {10,30,60,100,150}).

2. **Cumulative Product**:
   Multiply values progressively:
   `=SCAN(1, A1:A5, LAMBDA(acc, x, acc * x))`
   The SCAN starts at 1 and multiplies each value into the accumulator.
   **Result**: An array of cumulative products (e.g., {1,2,3,4,5} returns {1,2,6,24,120}).

3. **Running Maximum**:
   Track the highest value seen so far:
   `=SCAN(-1E+308, A1:A5, LAMBDA(acc, x, IF(x > acc, x, acc)))`
   The SCAN keeps the larger of the accumulator and each element.
   **Result**: An array where each value is the maximum up to that point (e.g., {3,1,4,1,5} returns {3,3,4,4,5}).

4. **Progressive Text Concatenation**:
   Build a growing comma-separated string:
   `=SCAN("", A1:A4, LAMBDA(acc, x, IF(acc = "", x, acc & ", " & x)))`
   The SCAN appends each element with a comma separator.
   **Result**: An array of progressively longer strings (e.g., {"Alice", "Alice, Bob", "Alice, Bob, Carol", "Alice, Bob, Carol, Dave"}).

5. **Conditional Running Count**:
   Count how many values exceed a threshold at each step:
   `=SCAN(0, A1:A10, LAMBDA(acc, x, IF(x > 50, acc + 1, acc)))`
   The SCAN increments the accumulator only when a value exceeds 50.
   **Result**: An array showing the running count of values greater than 50 at each position.

6. **Cumulative Sum with LET**:
   Use LET inside the LAMBDA for clarity:
   `=SCAN(0, A1:A5, LAMBDA(acc, x, LET(weighted, x * 2, acc + weighted)))`
   The SCAN doubles each value before adding it to the accumulator.
   **Result**: An array of cumulative weighted sums (e.g., {1,2,3,4,5} returns {2,6,12,20,30}).

7. **Running Balance with Deposits and Withdrawals**:
   Track a bank balance over time where positive values are deposits and negative are withdrawals:
   `=SCAN(1000, A1:A6, LAMBDA(acc, x, acc + x))`
   The SCAN starts with an opening balance of 1000 and applies each transaction.
   **Result**: An array showing the balance after each transaction (e.g., if A1:A6 is {200,-50,100,-300,150,-75}, the result is {1200,1150,1250,950,1100,1025}).

### Notes:

- `SCAN` is available in Excel 365 and Excel 2024 or later versions.
- The LAMBDA must accept exactly two parameters: the first for the accumulator and the second for the current element.
- If the array is empty, SCAN returns an empty array.
- Elements are processed in row-major order: left to right across each row, then top to bottom across rows.
- The result array has the same dimensions as the input array.
- If the LAMBDA returns an error at any step, that element and all subsequent elements in the result will contain the error.
- The initial value is not included in the output array — only the accumulator values after processing each element are returned.

### Related Functions:

- **REDUCE**: Reduces an array to a single accumulated value by applying a LAMBDA cumulatively.
  Example: `=REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x))` sums the values.

- **MAP**: Applies a LAMBDA function to each element in an array, returning a new array.
  Example: `=MAP(A1:A5, LAMBDA(x, x * 2))` doubles each value.

- **LAMBDA**: Creates custom, reusable functions with user-defined parameters.
  Example: `=LAMBDA(x, x * 2)(5)` returns `10`.

- **LET**: Assigns names to calculation results within a formula, reducing repetition.
  Example: `=LET(x, 10, y, 20, x + y)` returns `30`.

### Summary:

The `SCAN` function is a powerful tool for building arrays of cumulative results by applying a LAMBDA function step by step across an array. While REDUCE collapses an array into a single final value, SCAN preserves every intermediate accumulator state, making it ideal for running totals, progressive aggregations, and any analysis where the step-by-step evolution of a calculation matters. Whether you need cumulative sums, running maximums, progressive concatenations, or custom incremental logic, SCAN provides a clean, functional approach to array-based cumulative computation.