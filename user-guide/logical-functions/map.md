<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MAP Function

The `MAP` function in Excel allows you to **apply a LAMBDA function to each element** in one or more arrays, returning a new array of the results. Instead of writing helper columns or complex array formulas, you can transform every value in a range with a single, readable formula.

MAP is particularly useful for applying custom transformations, calculations, or formatting to entire ranges at once. It pairs naturally with LAMBDA to create concise, expressive data pipelines directly within your formulas.

### Key Features of MAP:

- Apply a custom LAMBDA function to every element of an array.
- Accept multiple arrays of the same size and process corresponding elements together.
- Return a new array with the same dimensions as the input.
- Eliminate the need for helper columns when transforming data.
- Combine with other functions like IF, LET, and TEXT inside the LAMBDA for complex transformations.

### Syntax:

```plaintext
MAP(array1, [array2, …], lambda)
```

- **array1** (required): The first array or range to map over.
- **array2, …** (optional): Additional arrays or ranges. All arrays must have the same dimensions.
- **lambda** (required): A LAMBDA function that is called for each element (or set of corresponding elements) in the input arrays. The number of LAMBDA parameters must match the number of arrays provided.

### How MAP Works:

The `MAP` function processes its arguments as follows:

1. Takes one or more arrays of the same dimensions.
2. Iterates through each element (or set of corresponding elements across arrays).
3. Passes the element(s) to the provided LAMBDA function.
4. Collects each LAMBDA result into a new array.
5. Returns the resulting array with the same dimensions as the input.

Each element is processed independently, and the LAMBDA is called once per element (or per set of corresponding elements).

### Examples:

1. **Double Every Value in a Range**:
   Apply a simple transformation to each element:
   `=MAP(A1:A5, LAMBDA(x, x * 2))`
   The MAP passes each value in `A1:A5` to the LAMBDA, which doubles it.
   **Result**: An array where each value is doubled (e.g., if A1:A5 is {1,2,3,4,5}, the result is {2,4,6,8,10}).

2. **Convert Temperatures from Celsius to Fahrenheit**:
   Transform a column of Celsius values:
   `=MAP(A1:A5, LAMBDA(c, c * 9/5 + 32))`
   The MAP converts each Celsius value to Fahrenheit.
   **Result**: An array of Fahrenheit values (e.g., {0,10,20,30,100} becomes {32,50,68,86,212}).

3. **Apply Conditional Logic to Each Element**:
   Use IF inside the LAMBDA to classify values:
   `=MAP(A1:A5, LAMBDA(x, IF(x >= 50, "Pass", "Fail")))`
   The MAP checks each value and returns "Pass" or "Fail".
   **Result**: An array of "Pass" or "Fail" strings based on each value.

4. **Using Multiple Arrays**:
   Combine corresponding elements from two ranges:
   `=MAP(A1:A5, B1:B5, LAMBDA(price, qty, price * qty))`
   The MAP multiplies each price by its corresponding quantity.
   **Result**: An array of totals (e.g., if prices are {10,20,30} and quantities are {2,3,1}, the result is {20,60,30}).

5. **Format Text from a Range**:
   Apply text transformations to each element:
   `=MAP(A1:A5, LAMBDA(name, UPPER(LEFT(name, 1)) & LOWER(MID(name, 2, LEN(name) - 1))))`
   The MAP capitalizes the first letter of each name and lowercases the rest.
   **Result**: An array of properly capitalized names.

6. **Calculate Tax for Each Price**:
   Apply a tax calculation to every item:
   `=MAP(A1:A10, LAMBDA(price, ROUND(price * 1.08, 2)))`
   The MAP adds 8% tax to each price and rounds to 2 decimal places.
   **Result**: An array of prices with tax applied.

7. **Combine MAP with LET**:
   Use LET inside the LAMBDA for clarity:
   `=MAP(A1:A5, LAMBDA(x, LET(doubled, x * 2, IF(doubled > 100, "High", "Low"))))`
   The MAP doubles each value and classifies the result.
   **Result**: An array of "High" or "Low" based on the doubled value.

### Notes:

- `MAP` is available in Excel 365 and Excel 2024 or later versions.
- All input arrays must have the same number of rows and columns; otherwise, MAP returns a `#VALUE!` error.
- The number of parameters in the LAMBDA must match the number of arrays passed to MAP.
- MAP always returns an array with the same dimensions as the input arrays.
- If the LAMBDA returns an error for any element, that element in the result array will contain the error.
- MAP can be combined with other dynamic array functions like FILTER, SORT, and UNIQUE for powerful data transformations.

### Related Functions:

- **LAMBDA**: Creates custom, reusable functions with user-defined parameters.
  Example: `=LAMBDA(x, x * 2)(5)` returns `10`.

- **LET**: Assigns names to calculation results within a formula, reducing repetition.
  Example: `=LET(x, 10, y, 20, x + y)` returns `30`.

- **REDUCE**: Reduces an array to a single value by applying a LAMBDA cumulatively.
  Example: `=REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x))` sums the values.

- **IF**: Performs conditional logic based on a test.
  Example: `=IF(A1 > 50, "High", "Low")`

### Summary:

The `MAP` function is a powerful tool for transforming arrays by applying a LAMBDA function to each element. It eliminates the need for helper columns and complex array formulas, making data transformations concise and readable. Whether you need to convert units, apply conditional logic, combine multiple ranges, or perform custom calculations across a dataset, MAP provides a clean, functional approach to array processing.