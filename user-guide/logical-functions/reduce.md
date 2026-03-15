<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## REDUCE Function

The `REDUCE` function in Excel allows you to **reduce an array to a single accumulated value** by applying a LAMBDA function cumulatively to each element. Starting from an initial value, REDUCE processes each element in order, carrying forward the result from the previous step as an accumulator.

REDUCE is particularly useful for aggregating data in custom ways that go beyond what built-in functions like SUM or PRODUCT offer. It pairs naturally with LAMBDA to express iterative accumulation logic directly within a single formula, without helper columns or VBA.

### Key Features of REDUCE:

- Accumulate an array into a single result by applying a LAMBDA function to each element in order.
- Start from a user-defined initial value that acts as the accumulator's seed.
- Access both the running accumulator and the current element in each step of the reduction.
- Implement custom aggregation logic beyond what standard functions provide.
- Combine with other functions like IF, LET, and TEXT inside the LAMBDA for complex accumulation patterns.

### Syntax:

```plaintext
REDUCE(initial_value, array, lambda)
```

- **initial_value** (required): The starting value for the accumulator. This is the value passed to the LAMBDA on the first iteration before any array elements are processed.
- **array** (required): The array or range to reduce. Elements are processed in row-major order (left to right, top to bottom).
- **lambda** (required): A LAMBDA function with exactly two parameters. The first parameter receives the current accumulator value and the second receives the current array element. The LAMBDA must return the updated accumulator value.

### How REDUCE Works:

The `REDUCE` function processes its arguments as follows:

1. Sets the accumulator to the provided `initial_value`.
2. Takes the first element of the array and calls the LAMBDA with the accumulator and that element.
3. The LAMBDA's return value becomes the new accumulator.
4. Repeats for each subsequent element in the array, passing the updated accumulator and the next element.
5. After all elements have been processed, returns the final accumulator value.

Each element is processed in order, and the accumulator carries the running result through every step.

### Examples:

1. **Sum All Values in a Range**:
   Replicate SUM behavior using REDUCE:
   `=REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x))`
   The REDUCE starts at 0 and adds each value in `A1:A5` to the accumulator.
   **Result**: The sum of all values (e.g., if A1:A5 is {1,2,3,4,5}, the result is 15).

2. **Product of All Values**:
   Multiply all elements together:
   `=REDUCE(1, A1:A5, LAMBDA(acc, x, acc * x))`
   The REDUCE starts at 1 and multiplies each value into the accumulator.
   **Result**: The product of all values (e.g., {1,2,3,4,5} returns 120).

3. **Count Values That Meet a Condition**:
   Count how many values exceed a threshold:
   `=REDUCE(0, A1:A10, LAMBDA(acc, x, IF(x > 50, acc + 1, acc)))`
   The REDUCE increments the accumulator only when a value exceeds 50.
   **Result**: The count of values greater than 50.

4. **Concatenate Text with a Delimiter**:
   Join all values into a single comma-separated string:
   `=REDUCE("", A1:A5, LAMBDA(acc, x, IF(acc = "", x, acc & ", " & x)))`
   The REDUCE builds a string by appending each element with a comma separator.
   **Result**: A comma-separated string (e.g., "Alice, Bob, Carol, Dave, Eve").

5. **Find the Maximum Value**:
   Determine the largest value in a range without using MAX:
   `=REDUCE(-1E+308, A1:A10, LAMBDA(acc, x, IF(x > acc, x, acc)))`
   The REDUCE starts with a very small number and keeps the larger of the accumulator and each element.
   **Result**: The maximum value in the range.

6. **Running Calculation with LET**:
   Use LET inside the LAMBDA for clarity:
   `=REDUCE(0, A1:A5, LAMBDA(acc, x, LET(weighted, x * 2, acc + weighted)))`
   The REDUCE doubles each value before adding it to the accumulator.
   **Result**: The sum of doubled values (e.g., {1,2,3,4,5} returns 30).

7. **Conditional Sum**:
   Sum only values that meet a specific criterion:
   `=REDUCE(0, A1:A10, LAMBDA(acc, x, IF(x >= 0, acc + x, acc)))`
   The REDUCE adds only non-negative values to the accumulator.
   **Result**: The sum of all non-negative values in the range.

### Notes:

- `REDUCE` is available in Excel 365 and Excel 2024 or later versions.
- The LAMBDA must accept exactly two parameters: the first for the accumulator and the second for the current element.
- If the array is empty, REDUCE returns the `initial_value` unchanged.
- Elements are processed in row-major order: left to right across each row, then top to bottom across rows.
- If the LAMBDA returns an error at any step, REDUCE stops and returns that error.
- The initial value can be any data type — a number, string, array, or Boolean — depending on the accumulation logic.

### Related Functions:

- **LAMBDA**: Creates custom, reusable functions with user-defined parameters.
  Example: `=LAMBDA(x, x * 2)(5)` returns `10`.

- **MAP**: Applies a LAMBDA function to each element in an array, returning a new array.
  Example: `=MAP(A1:A5, LAMBDA(x, x * 2))` doubles each value.

- **LET**: Assigns names to calculation results within a formula, reducing repetition.
  Example: `=LET(x, 10, y, 20, x + y)` returns `30`.

- **SUM**: Adds all numbers in a range.
  Example: `=SUM(A1:A10)` returns the total.

### Summary:

The `REDUCE` function is a powerful tool for accumulating an array into a single value by applying a LAMBDA function step by step. It goes beyond built-in aggregation functions like SUM and PRODUCT by allowing fully custom accumulation logic — from conditional sums and string concatenation to finding extremes and building complex derived values. Whether you need custom aggregation, iterative calculations, or flexible data reduction, REDUCE provides a clean, functional approach to processing arrays one element at a time.