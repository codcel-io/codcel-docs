<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

##IFS Function

Introduced in Excel 2016, the `IFS` function is a more streamlined alternative to the nested `IF` function. It checks multiple conditions and returns a value corresponding to the first true condition.

### Syntax:

    IFS(condition1, value1, condition2, value2, ...)

- **condition1, condition2, ...**: These are the conditions that the function checks.
- **value1, value2, ...**: These are the values that are returned if the corresponding condition is `TRUE`.

### Examples:

1. `=IFS(A1 > 100, "High", A1 > 50, "Medium", A1 > 0, "Low")` would return `"High"` if `A1` is greater than 100, `"Medium"` if `A1` is greater than 50 but less than or equal to 100, and `"Low"` if `A1` is greater than 0 but less than or equal to 50.
2. `=IFS(B1 = "Apple", "Fruit", B1 = "Carrot", "Vegetable", B1 = "Chicken", "Meat")` would categorize the item in `B1` as `"Fruit"`, `"Vegetable"`, or `"Meat"` based on the specific match.

### Usage Notes:
- `IFS` is useful for situations where you have multiple conditions to check. It simplifies the formula compared to multiple nested `IF` statements.
- The function evaluates each condition in the order provided, and once it finds a `TRUE` condition, it returns the corresponding value and doesn't evaluate any further conditions.
- If none of the conditions are met and no default condition is provided, the `IFS` function will return the `#N/A` error.

> **Note**: When using `IFS`, ensure you cover all possible scenarios you expect in your data to avoid the `#N/A` error. You can include a final `TRUE` condition at the end of the `IFS` function as a catch-all to handle any unexpected values.