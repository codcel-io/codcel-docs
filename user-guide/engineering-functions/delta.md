<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DELTA Function

The `DELTA` function in Excel is used to test whether two numbers are equal. It returns `1` if the numbers are equal and
`0` otherwise. This function is especially useful in mathematical or logical computations where a binary result is
required.

### Key Features of DELTA:

- Compares two numeric values for equality.
- Returns a binary result (`1` for equal, `0` for not equal).
- Can also be used to filter or select data based on equality conditions.

### Syntax:

```plaintext
DELTA(number1, [number2])
```

- **number1**: The first numeric value to compare. This argument is required.
- **number2** (optional): The second numeric value to compare. If omitted, it defaults to `0`.

### Examples:

1. **Compare Equal Numbers**:  
   `=DELTA(5, 5)`  
   Compares `5` and `5`.  
   **Result**: `1`

2. **Compare Unequal Numbers**:  
   `=DELTA(7, 10)`  
   Compares `7` and `10`.  
   **Result**: `0`

3. **Compare with Default `number2` (`0`)**:  
   `=DELTA(3)`  
   Compares `3` and `0` since the second argument is omitted.  
   **Result**: `0`

4. **Compare Floating-Point Values**:  
   `=DELTA(3.14, 3.14)`  
   Compares two floating-point numbers for equality.  
   **Result**: `1`

5. **Test Negative Values**:  
   `=DELTA(-4, -4)`  
   Compares `-4` with `-4`.  
   **Result**: `1`

### Notes:

- The `DELTA` function works with numerical data only.  
  If non-numeric arguments are provided, Excel returns a `#VALUE!` error.

- **Automatic Default Argument**:  
  If the `number2` argument is not provided, it is assumed to be `0`.

- **Binary Output**:  
  Regardless of the input values, the function always returns `1` or `0`.

### Applications:

- **Data Validation**:  
  Use `DELTA` to ensure numeric data matches specified criteria.

- **Logical Filters**:  
  Include `DELTA` within larger calculations to flag matching or mismatching values.

- **Engineering and Boolean Logic**:  
  In combination with other mathematical functions, it can help streamline logic-based or decision-making processes.

- **Statistical Operations**:  
  Test data for specific characteristics or consistency (e.g., ensuring certain values are identical).

### Complementary Functions:

- **IF**: Use in conjunction with `DELTA` to perform conditional actions based on equality.  
  Example:  
  `=IF(DELTA(A1, B1), "Equal", "Not Equal")`

- **AND/OR**: Combine `DELTA` results for more complex logical checks.

- **ABS**, `ROUND`: Use these functions to handle floating-point precision before comparison if needed.

### Summary:

The `DELTA` function is a simple yet powerful way to check for numeric equality in Excel. It ensures efficient testing
of values, making it a handy tool in applications involving logic, mathematics, and statistics.