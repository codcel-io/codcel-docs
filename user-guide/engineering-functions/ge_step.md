<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GESTEP Function

The `GESTEP` function in Excel evaluates whether a given number is greater than or equal to a specified step value. It
returns `1` if the number is greater than or equal to the step value, and `0` otherwise. This function is useful for
conditional evaluations, logic-based calculations, or comparisons in engineering and mathematical problems.

### Key Features of GESTEP:

- Compares a given number against a step value and returns `1` if the number is **greater than or equal to** the step
  value.
- Useful in scenarios that require thresholds or step-based evaluations.
- Includes an optional second argument for specifying the step value, with a default of `0`.

### Syntax:

```plaintext
GESTEP(number, [step])
```

- **number**: The value you want to test against the step value. This is a required numeric argument.
- **step**: (Optional) The threshold value for comparison. If omitted, the default step value is `0`.

### Examples:

1. **Compare a Number Greater Than the Step Value**:  
   `=GESTEP(5, 3)`  
   Tests if `5` is greater than or equal to `3`.  
   **Result**: `1`

2. **Compare a Number Less Than the Step Value**:  
   `=GESTEP(2, 3)`  
   Tests if `2` is greater than or equal to `3`.  
   **Result**: `0`

3. **Use the Default Step Value (`0`)**:  
   `=GESTEP(-1)`  
   Tests if `-1` is greater than or equal to `0`.  
   **Result**: `0`

4. **Compare Zero Against a Non-Zero Step Value**:  
   `=GESTEP(0, -3)`  
   Tests if `0` is greater than or equal to `-3`.  
   **Result**: `1`

### Notes:

- The function will return a `#VALUE!` error if either argument is non-numeric.
- The step value is optional—if not specified, it is automatically set to `0`.
- Primarily used in conditional logic scenarios, such as when evaluating thresholds or limits, particularly in
  engineering and mathematical models.

### Applications:

- **Engineering**: Used to check if values meet or exceed certain thresholds, such as signal levels or tolerances.
- **Mathematics**: Helps determine if a number satisfies predefined step conditions.
- **Logical Calculations**: Often applied where binary outputs (`1` or `0`) are preferred for decisions or evaluations.

### Related Functions:

- **IF**: A more general conditional function that can evaluate conditions and return different results based on the
  outcome.  
  Example: `=IF(A1>=3, 1, 0)`
- **SIGN**: Returns `1`, `0`, or `-1`, depending on the sign of the provided number.  
  Example: `=SIGN(-5)`

### Summary:

The `GESTEP` function is a simple and effective tool for comparing a value against a step threshold, commonly used in
logic-based operations, engineering, and mathematics. It returns `1` when the condition is satisfied and `0` otherwise,
making it ideal for binary decision-making processes.