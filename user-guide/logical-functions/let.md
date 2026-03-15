<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LET Function

The `LET` function in Excel allows you to **assign names to calculation results** within a formula. This reduces repetition, improves formula readability, and can enhance performance by avoiding redundant calculations.

Instead of repeating the same expression multiple times in a complex formula, you can define it once with a meaningful name and reference that name throughout. This makes formulas easier to read, debug, and maintain.

### Key Features of LET:

- Assign names to values or expressions within a single formula.
- Reduce redundant calculations by computing a value once and reusing it.
- Improve formula readability with descriptive variable names.
- Support multiple name-value pairs in a single LET call.
- Can be nested within other functions or contain nested functions.

### Syntax:

```plaintext
LET(name1, value1, [name2, value2, …], calculation)
```

- **name1, name2, …**: The names to assign. Names must start with a letter and cannot be cell references or reserved words.
- **value1, value2, …**: The values or expressions to assign to each name. These are calculated once and can be referenced in subsequent name-value pairs or the final calculation.
- **calculation**: The formula or expression that uses the defined names. This is the return value of the LET function.

### How LET Works:

The `LET` function processes its arguments in order:

1. Evaluates `value1` and assigns it to `name1`.
2. Evaluates `value2` (which can reference `name1`) and assigns it to `name2`.
3. Continues for any additional name-value pairs.
4. Evaluates the final `calculation` expression using all defined names.
5. Returns the result of the calculation.

Each value is computed only once, even if its name appears multiple times in the formula.

### Examples:

1. **Simple Variable Assignment**:
   Assign a value to a name and use it in a calculation:
   `=LET(x, 10, x * 2)`
   The LET assigns `10` to `x`, then calculates `x * 2`.
   **Result**: `20`

2. **Multiple Variables**:
   Define multiple names and use them together:
   `=LET(a, 5, b, 3, a + b)`
   The LET assigns `5` to `a` and `3` to `b`, then adds them.
   **Result**: `8`

3. **Avoiding Redundant Calculations**:
   Calculate a sum once and use it multiple times:
   `=LET(total, SUM(A1:A10), IF(total > 100, total * 0.1, total * 0.05))`
   The LET calculates the sum once and references it twice in the IF statement.
   **Result**: Discount based on total (10% if over 100, 5% otherwise)

4. **Using Cell References in Values**:
   If `A1 = 100` and `B1 = 20`:
   `=LET(price, A1, discount, B1, price - (price * discount / 100))`
   The LET calculates the discounted price.
   **Result**: `80`

5. **Nested Functions Inside LET**:
   Combine LET with other functions for complex calculations:
   `=LET(avg, AVERAGE(A1:A10), stdev, STDEV(A1:A10), (B1 - avg) / stdev)`
   The LET calculates the z-score of `B1` relative to the data in `A1:A10`.
   **Result**: Z-score of B1

6. **Sequential Dependencies**:
   Later names can reference earlier ones:
   `=LET(base, 100, rate, 0.05, interest, base * rate, base + interest)`
   The LET calculates simple interest step by step.
   **Result**: `105`

7. **LET with Conditional Logic**:
   Use LET to simplify complex IF statements:
   `=LET(score, 75, pass_mark, 60, IF(score >= pass_mark, "Pass", "Fail"))`
   The LET evaluates whether the score meets the pass mark.
   **Result**: `Pass`

### Notes:

- `LET` is available in Excel 365 and Excel 2021 or later versions.
- You can define up to 126 name-value pairs in a single LET function.
- Names must be valid identifiers: they must start with a letter and cannot contain spaces or special characters.
- Names cannot be cell references (like `A1`) or reserved Excel names.
- If a name is used before it is defined, Excel returns a `#NAME?` error.
- LET can significantly improve performance in formulas that would otherwise calculate the same expression multiple times.

### Related Functions:

- **LAMBDA**: Creates custom, reusable functions with user-defined parameters.
  Example: `=LAMBDA(x, x * 2)(5)` returns `10`.

- **IF**: Performs conditional logic based on a test.
  Example: `=IF(A1 > 50, "High", "Low")`

- **SWITCH**: Evaluates an expression against a list of values and returns the matching result.
  Example: `=SWITCH(A1, 1, "One", 2, "Two", "Other")`

### Summary:

The `LET` function is a powerful tool for simplifying complex formulas by assigning names to intermediate calculations. It improves readability by replacing repeated expressions with descriptive names, enhances performance by ensuring values are calculated only once, and makes formulas easier to maintain and debug. Whether you're building financial models, data transformations, or conditional logic, LET helps keep your formulas clean and efficient.