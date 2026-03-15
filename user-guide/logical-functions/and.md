<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## AND Function

The `AND` function in Excel is a logical function used to test multiple conditions and return `TRUE` only if **all the
conditions are true**. If any of the conditions are false, the function returns `FALSE`.

This function is particularly useful in decision-making processes, combining multiple criteria, or creating conditional
formulas for analytical purposes.

### Key Features of AND:

- Evaluates one or more logical conditions.
- Returns `TRUE` if **all** conditions are met, otherwise returns `FALSE`.
- Commonly used in combination with other functions like `IF` to build complex logical statements.

### Syntax:

```plaintext
AND(logical1, [logical2], …)
```

- **logical1, logical2, …**: The conditions you want to test. These can be:
    - Logical expressions (e.g., `A1>10` or `B2="Yes"`).
    - References to cells containing logical values.
    - Functions that return logical values (`TRUE` or `FALSE`).

### Formula and Logical Operation:

The `AND` function evaluates the logical conditions using the formula:

```plaintext
AND(condition1, condition2, …)
```

Where:

- Returns `TRUE` if all conditions evaluate to `TRUE`.
- Returns `FALSE` if **any** condition evaluates to `FALSE`.

### Examples:

1. **Simple Logical AND**:  
   `=AND(5 > 3, 7 > 2)`  
   Both conditions are true, so the result is:  
   **Result**: `TRUE`

2. **Combining Logical Conditions with Cell References**:  
   If `A1 = 10` and `B1 = "Yes"`, then:  
   `=AND(A1 > 5, B1 = "Yes")`  
   Both conditions are satisfied, so the result is:  
   **Result**: `TRUE`

3. **Using AND with the IF Function**:  
   Suppose `C1 = 50`, `C2 = 100`, and you want to return "Pass" if both values meet the criteria `C1 > 40` and
   `C2 > 90`:  
   `=IF(AND(C1 > 40, C2 > 90), "Pass", "Fail")`  
   Both conditions are true, so the result is:  
   **Result**: `Pass`

4. **Testing Multiple Conditions**:  
   `=AND(A1 > 10, B1 < 5, C1 = "Completed")`  
   If any condition is not met, the function returns:  
   **Result**: `FALSE`

5. **Checking for Logical Values in Cells**:  
   If `A1` contains `TRUE` and `B1` contains `FALSE`, then:  
   `=AND(A1, B1)`  
   The result is:  
   **Result**: `FALSE`

### Notes:

- `AND` will ignore empty cells unless explicitly referenced in a condition.
- Outputs `#VALUE!` error if logical conditions contain invalid inputs (e.g., text that cannot be interpreted as logic).
- Logical values `TRUE` and `FALSE` are treated as `1` and `0` respectively in mathematical operations.
- Can evaluate up to 255 conditions (or 30 in older Excel versions).

### Related Functions:

- **OR**: Returns `TRUE` if any condition is true.  
  Example: `=OR(A1 > 10, B1 < 5)`  
  Returns `TRUE` if at least one condition evaluates to `TRUE`.

- **IF**: Performs conditional operations based on a logical test.  
  Example: `=IF(AND(A1 > 50, B1 < 100), "Valid", "Invalid")`

- **NOT**: Reverses a logical value.  
  Example: `=NOT(AND(A1 > 10, B1 < 20))`

### Summary:

The `AND` function is a simple but essential tool in Excel for evaluating multiple conditions simultaneously. It allows
users to model complex decision-making processes in formulas, making it highly valuable for data analysis, reporting,
and logical simulations.