<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## EXP Function

The `EXP` function in Excel is used to calculate the value of **e (Euler's number)** raised to the power of a given
number. Euler's number, **e**, is approximately equal to `2.71828182845904`, and it is the base of natural logarithms.

Mathematically, it can be expressed as:

    EXP(x) = e^x

where **x** is the exponent to which Euler's number is raised.

This function is particularly useful in mathematics, statistics, engineering, and financial applications, especially for
calculations involving exponential growth or decay.

### Syntax:

    EXP(number)

- **number**: This is a required argument. It specifies the exponent to which the base `e` should be raised.

### Key Points:

- The `EXP` function operates on **real numbers**.
- If the `number` is `0`, the `EXP` function will always return `1` because any number raised to the power of `0` equals
  `1`.
- For positive values of `number`, the result will be greater than `1`.
- For negative values of `number`, the result will be between `0` and `1`.
- The `EXP` function is valuable for modeling natural exponential processes, such as compound interest or population
  growth.

### Examples:

1. `=EXP(1)`  
   Calculates **e** raised to the power of `1`.  
   **Result**: `2.71828`

2. `=EXP(0)`  
   Calculates **e** raised to the power of `0`.  
   **Result**: `1`

3. `=EXP(-2)`  
   Calculates **e** raised to the power of `-2`.  
   **Result**: `0.13534`

4. `=EXP(2.5)`  
   Calculates **e** raised to the power of `2.5`.  
   **Result**: `12.18249`

### Notes:

- The `EXP` function returns highly precise values for a wide range of input values, as it is implemented using
  floating-point arithmetic.
- Pair the `EXP` function with the `LN` function to reverse the operation:

  For example:  
  `=LN(EXP(3))`  
  **Result**: `3`

- The `EXP` function is especially suitable for dealing with exponential distributions, growth rates, and natural
  logarithms.

> **Tip**: Use `EXP` for solving growth-related equations or when performing statistical or computational operations
requiring exponential calculations.