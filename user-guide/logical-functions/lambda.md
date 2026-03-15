<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LAMBDA Function

The `LAMBDA` function in Excel allows you to create **custom, reusable functions** by defining parameters and a calculation formula. Instead of writing the same complex formula repeatedly, you can encapsulate the logic into a LAMBDA and call it with different inputs.

This function is particularly useful for creating modular formulas, simplifying complex calculations, and building self-documenting spreadsheets where custom logic is clearly named and organized.

### Key Features of LAMBDA:

- Define custom functions with one or more named parameters.
- Encapsulate complex logic into a single, reusable formula.
- Can be called inline or, in Excel, saved as a named function via the Name Manager.
- Supports recursive definitions for iterative calculations.
- Makes formulas more readable and maintainable.

### Syntax:

```plaintext
LAMBDA([parameter1, parameter2, …], calculation)
```

- **parameter1, parameter2, …** (optional): Named parameters that act as placeholders for values passed to the function. You can define up to 253 parameters.
- **calculation**: The formula or expression to execute using the defined parameters. This is the return value of the LAMBDA.

To call an inline LAMBDA immediately, append the arguments in parentheses:

```plaintext
LAMBDA(x, x * 2)(5)
```

### How LAMBDA Works:

The `LAMBDA` function creates a function object that:

1. Accepts the defined parameters as inputs.
2. Evaluates the calculation expression using those parameter values.
3. Returns the result of the calculation.

When used inline, you define the LAMBDA and immediately invoke it by passing arguments. In Excel, you can also save a LAMBDA to the Name Manager, allowing you to call it by name throughout your workbook.

### Examples:

1. **Simple Inline LAMBDA (Double a Number)**:
   Create a function that doubles the input value:
   `=LAMBDA(x, x * 2)(5)`
   The LAMBDA takes `x` as input, multiplies it by 2, and is called with `5`.
   **Result**: `10`

2. **Multiple Parameters (Calculate Area)**:
   Create a function that calculates the area of a rectangle:
   `=LAMBDA(length, width, length * width)(4, 6)`
   The LAMBDA accepts `length` and `width`, multiplies them, and is called with `4` and `6`.
   **Result**: `24`

3. **Using LAMBDA with Cell References**:
   If `A1 = 10` and `B1 = 3`, calculate the power:
   `=LAMBDA(base, exp, POWER(base, exp))(A1, B1)`
   The LAMBDA computes `A1` raised to the power of `B1`.
   **Result**: `1000`

4. **Nested Functions Inside LAMBDA**:
   Create a function that rounds a number to 2 decimal places after dividing:
   `=LAMBDA(a, b, ROUND(a / b, 2))(100, 3)`
   The LAMBDA divides `a` by `b` and rounds the result.
   **Result**: `33.33`

5. **LAMBDA with Conditional Logic**:
   Create a function that returns "Pass" or "Fail" based on a score threshold:
   `=LAMBDA(score, threshold, IF(score >= threshold, "Pass", "Fail"))(75, 60)`
   The LAMBDA checks if `score` meets the `threshold`.
   **Result**: `Pass`

### Notes:

- `LAMBDA` is available in Excel 365 and Excel 2021 or later versions.
- A LAMBDA without arguments in `calculation` returns a `#VALUE!` error when called.
- If you provide fewer arguments than defined parameters, the LAMBDA returns another LAMBDA (partial application), which may result in unexpected behavior if not intended.
- Recursive LAMBDAs (a LAMBDA calling itself) can be created by assigning the LAMBDA to a name and referencing that name within the calculation.
- The maximum number of parameters is 253.
- **Codcel Support**: Codcel supports both inline LAMBDA expressions and named LAMBDAs (functions saved to the Name Manager for reuse across a workbook), including recursive named LAMBDAs.

### Related Functions:

- **LET**: Assigns names to calculation results within a formula, reducing repetition.
  Example: `=LET(x, 10, y, 20, x + y)` returns `30`.

- **IF**: Performs conditional logic based on a test.
  Example: `=IF(A1 > 50, "High", "Low")`

- **MAP**: Applies a LAMBDA function to each element in an array.
  Example: `=MAP(A1:A5, LAMBDA(x, x * 2))` doubles each value in the range.

- **REDUCE**: Reduces an array to a single value using a LAMBDA function.
  Example: `=REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x))` sums the values.

### Summary:

The `LAMBDA` function is a powerful tool for creating custom, reusable functions directly within Excel formulas. It enables cleaner, more modular spreadsheet design by encapsulating complex logic into named parameters and calculations. Codcel fully supports both inline and named LAMBDA expressions, allowing you to simplify repetitive calculations and build more readable formulas.