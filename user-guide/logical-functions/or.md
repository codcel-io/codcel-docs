<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## OR Function

The `OR` function in Excel is a logical function used to test multiple conditions and return `TRUE` if **any of the
conditions are true**. If all the conditions are false, the function returns `FALSE`.

This function is particularly useful for decision-making processes, generating flexible logical conditions, or creating
conditional formulas that rely on one or more criteria being satisfied.

### Key Features of OR:

- Evaluates one or more logical conditions.
- Returns `TRUE` if **at least one** condition is met, otherwise returns `FALSE`.
- Commonly used in combination with other functions like `IF` to build complex logical statements.

### Syntax:

```plaintext
OR(logical1, [logical2], …)
```

- **logical1, logical2, …**: The conditions you want to test. These can be:
    - Logical expressions (e.g., `A1>10` or `B2="Yes"`).
    - References to cells containing logical values.
    - Functions that return logical values (`TRUE` or `FALSE`).

### Formula and Logical Operation:

The `OR` function evaluates the logical conditions using the formula:

```plaintext
OR(condition1, condition2, …)
```

Where:

- Returns `TRUE` if **any** condition evaluates to `TRUE`.
- Returns `FALSE` if **all** conditions evaluate to `FALSE`.

### Examples:

1. **Simple Logical OR**:  
   `=OR(5 > 3, 7 < 2)`  
   At least one condition is true, so the result is:  
   **Result**: `TRUE`

2. **Combining Logical Conditions with Cell References**:  
   If `A1 = 10` and `B1 = "No"`, then:  
   `=OR(A1 > 5, B1 = "Yes")`  
   One condition is satisfied (`A1 > 5`), so the result is:  
   **Result**: `TRUE`

3. **Using OR with the IF Function**:  
   Suppose `C1 = 30`, `C2 = 70`, and you want to return "Valid" if either value meets the criteria `C1 > 50` or
   `C2 > 50`:  
   `=IF(OR(C1 > 50, C2 > 50), "Valid", "Invalid")`  
   One of the conditions is true (`C2 > 50`), so the result is:  
   **Result**: `Valid`

4. **Testing Multiple Conditions**:  
   `=OR(A1 > 10, B1 < 5, C1 = "In Progress")`  
   If any of the conditions are met, the function returns:  
   **Result**: `TRUE`

5. **Checking for Logical Values in Cells**:  
   If `A1` contains `FALSE` and `B1` contains `TRUE`, then:  
   `=OR(A1, B1)`  
   The result is:  
   **Result**: `TRUE`

### Notes:

- `OR` will ignore empty cells unless explicitly referenced in a condition.
- Outputs `#VALUE!` error if logical conditions contain invalid inputs (e.g., text that cannot be interpreted as logic).
- Logical values `TRUE` and `FALSE` are treated as `1` and `0` respectively in mathematical operations.
- Can evaluate up to 255 conditions (or 30 in older Excel versions).

### Related Functions:

- **AND**: Returns `TRUE` if all conditions are true.  
  Example: `=AND(A1 > 10, B1 < 5)`  
  Returns `TRUE` only if all conditions evaluate to `TRUE`.

- **IF**: Performs conditional operations based on a logical test.  
  Example: `=IF(OR(A1 > 50, B1 < 100), "Possible", "Not Possible")`

- **NOT**: Reverses a logical value.  
  Example: `=NOT(OR(A1 > 10, B1 < 20))`

### Summary:

The `OR` function is a powerful and flexible tool in Excel for evaluating multiple conditions. By returning `TRUE` when
any condition is met, it allows users to create robust and dynamic formulas for data analysis, decision-making, and
automated reporting scenarios.