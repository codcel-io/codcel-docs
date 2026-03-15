<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SWITCH Function

The `SWITCH` function in Excel evaluates an expression against a list of values and returns the result corresponding to the **first matching value**. If no match is found, it can return an optional default value.

This function is particularly useful for replacing multiple nested `IF` statements when you need to compare a single expression against several possible values, making formulas more readable and easier to maintain.

### Key Features of SWITCH:

- Evaluates one expression against multiple defined values.
- Returns the result associated with the first matching value.
- Supports an optional default value if no matches are found.
- Makes formulas more readable and compact compared to nested `IF` statements.
- Evaluates the expression only once, improving efficiency over repeated `IF` tests.

### Syntax:

```plaintext
SWITCH(expression, value1, result1, [value2, result2], …, [default])
```

- **expression**: The value or formula being evaluated. This is compared against each value in order.
- **value1, value2, …**: The values to compare against the expression. Each value is tested sequentially.
- **result1, result2, …**: The corresponding result to return when the expression matches the associated value.
- **default** (optional): The value returned if no values match the expression. If omitted and no match is found, the function returns a `#N/A` error.

### How SWITCH Works:

The `SWITCH` function processes its arguments in sequence:

1. Evaluates the **expression** once.
2. Compares the expression to **value1**. If they match, returns **result1**.
3. If no match, compares the expression to **value2**. If they match, returns **result2**.
4. Continues comparing against each subsequent value-result pair.
5. If no values match and a **default** is provided, returns the default.
6. If no values match and no default is provided, returns a `#N/A` error.

The function stops as soon as it finds the first match and does not evaluate remaining value-result pairs.

### Examples:

1. **Simple Value Matching**:
   Suppose cell `A1` contains a numeric grade code (1 for "A", 2 for "B", 3 for "C"):
   `=SWITCH(A1, 1, "A", 2, "B", 3, "C")`
   If `A1 = 2`, the expression matches the second value.
   **Result**: `B`

2. **Using a Default Value**:
   Convert product codes to product names, with a fallback for unknown codes:
   `=SWITCH(B1, "P1", "Apples", "P2", "Oranges", "P3", "Bananas", "Unknown Product")`
   If `B1 = "P2"`, the result is `"Oranges"`. If `B1 = "P4"`, no values match.
   **Result**: `Unknown Product`

3. **Day of Week Lookup**:
   Convert a day number into a day name:
   `=SWITCH(WEEKDAY(A1), 1, "Sunday", 2, "Monday", 3, "Tuesday", 4, "Wednesday", 5, "Thursday", 6, "Friday", 7, "Saturday")`
   If `A1` contains a date that falls on a Wednesday, the WEEKDAY returns `4`.
   **Result**: `Wednesday`

4. **Department Budget Allocation**:
   Assign budget percentages based on department codes:
   `=SWITCH(C1, "ENG", 0.30, "MKT", 0.25, "HR", 0.15, "OPS", 0.20, 0.10)`
   If `C1 = "MKT"`, the expression matches the second value.
   **Result**: `0.25`

5. **Combining SWITCH with Other Functions**:
   Use SWITCH inside a calculation to apply different tax rates:
   `=D1 * SWITCH(E1, "CA", 0.0725, "TX", 0.0625, "NY", 0.08, 0.05)`
   If `D1 = 100` and `E1 = "NY"`, SWITCH returns `0.08`.
   **Result**: `8`

6. **Using TRUE as the Expression**:
   Use `TRUE` as the expression to evaluate conditions similar to `IFS`:
   `=SWITCH(TRUE, A1 >= 90, "Excellent", A1 >= 70, "Good", A1 >= 50, "Average", "Poor")`
   If `A1 = 85`, the first match is `A1 >= 70`.
   **Result**: `Good`

7. **No Match Without Default**:
   When no default is provided and no values match:
   `=SWITCH(A1, "X", "Option 1", "Y", "Option 2")`
   If `A1 = "Z"`, no values match and no default is provided.
   **Result**: `#N/A`

### Notes:

- `SWITCH` is available in Excel 2019, Excel 365, and later versions.
- The function stops evaluating as soon as it finds the first match. Subsequent value-result pairs are not tested.
- The **expression** is evaluated only once, making SWITCH more efficient than equivalent nested `IF` statements.
- Values are compared in the order they are listed. Place the most likely matches first for optimal readability.
- Unlike `IF`, SWITCH does not directly support range comparisons (e.g., `A1 > 10`). To test ranges, use `TRUE` as the expression with conditional values, or use the `IFS` function instead.
- You can include up to 126 value-result pairs in a single SWITCH function.
- If the total number of arguments after the expression is odd, the last argument is treated as the default value.

### Related Functions:

- **IF**: Performs conditional logic based on a single test.
  Example: `=IF(A1 > 50, "Pass", "Fail")`

- **IFS**: Evaluates multiple conditions and returns the result for the first TRUE condition.
  Example: `=IFS(A1 >= 90, "A", A1 >= 80, "B", A1 >= 70, "C")`

- **CHOOSE**: Selects a value from a list based on a numeric index.
  Example: `=CHOOSE(2, "Red", "Blue", "Green")` returns `"Blue"`.

- **LET**: Assigns names to calculation results within a formula, reducing repetition.
  Example: `=LET(x, 10, x * 2)` returns `20`.

### Summary:

The `SWITCH` function is a powerful tool for simplifying formulas that compare a single expression against multiple possible values. It replaces complex nested `IF` statements with a clean, readable structure that is easier to write, debug, and maintain.

Whether you are mapping codes to labels, assigning categories based on values, or building lookup logic directly in a formula, SWITCH provides a concise and efficient approach. By evaluating the expression only once and stopping at the first match, it also offers a performance advantage over equivalent nested `IF` constructions.