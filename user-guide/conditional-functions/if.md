<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## IF Function

The `IF` function in Excel is one of the most fundamental logical functions. It checks whether a condition is met and returns one value if the condition is `TRUE` and another value if the condition is `FALSE`.

### Syntax:

    IF(logical_test, value_if_true, [value_if_false])

- **logical_test**: The condition you want to test.
- **value_if_true**: The value that is returned if the `logical_test` is `TRUE`.
- **value_if_false** (optional): The value that is returned if the `logical_test` is `FALSE`. If omitted, `FALSE` is returned.

### Examples:

1. `=IF(A1 > 10, "High", "Low")` checks if the value in cell `A1` is greater than 10. If it is, the function returns `"High"`, otherwise, it returns `"Low"`.
2. `=IF(B1 = "Apple", 5, 2)` would return `5` if cell `B1` contains the word `"Apple"`, and `2` otherwise.
3. `=IF(C1, "Done", "Not Done")` assumes `C1` contains a logical value (TRUE or FALSE). It returns `"Done"` if `C1` is TRUE and `"Not Done"` if `C1` is FALSE.

### Usage Notes:
- The `IF` function is extremely versatile and can be nested to evaluate multiple conditions.
- It is often used in combination with other functions like `AND`, `OR`, `MATCH`, etc., to create more complex logical tests.

> **Note**: Excel also provides `IFS` function in newer versions, which can handle multiple conditions without requiring nested `IF` statements.