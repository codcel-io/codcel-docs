<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ERF Function

The `ERF` function in Excel calculates the error function, which is a mathematical function used in statistics and
engineering to measure probabilities for normal distribution and analyze error rates. It returns the integral of the
error function between `0` and a given value.

### Key Features of ERF:

- Computes the error function's value to estimate probabilities or error outcomes.
- Integral calculation is helpful in normal distribution, signal processing, and probability analysis.
- Supports specifying an upper as well as lower limit for integration.

### Syntax:

```plaintext
ERF(lower_limit, [upper_limit])
```

- **lower_limit**: This argument represents the lower bound for the integral calculation of the error function. It is
  required.
- **upper_limit** (optional): This optional argument specifies the upper bound for the integral calculation. If omitted,
  Excel calculates the integral from `0` to the `lower_limit`.

### Examples:

1. **Calculate the Error Function for a Single Limit**:  
   `=ERF(1.5)`  
   Computes the error function from `0` to `1.5`.  
   **Result**: `0.966105146`

2. **Calculate the Error Function for Specified Limits**:  
   `=ERF(1, 2)`  
   Computes the error function from `1` to `2`.  
   **Result**: `0.136199847`

3. **Calculate the Error Function for Negative Limits**:  
   `=ERF(-1.5)`  
   Computes the error function from `0` to `-1.5`.  
   **Result**: `-0.966105146`

### Notes:

- The `ERF` function works with numeric inputs only. Passing non-numeric values results in a `#VALUE!` error.
- If the **lower_limit** or **upper_limit** are not within valid ranges or are missing, Excel may return an error or
  unexpected results.
- If **upper_limit** is omitted, the function assumes it is `0`.

### Applications:

- **Statistics and Probability**: Used in analyzing Gaussian (normal) distribution tables.
- **Signal Processing**: Helps in measuring error rates in communication and control systems.
- **Engineering**: Valuable for error analysis in various scientific and engineering fields.

### Complementary Functions:

- **ERFC**: The complementary error function (`1 - ERF(x)`).  
  Example: `=ERFC(1.5)`
- **NORM.DIST**: Works with normal distributions and probabilities, similar to `ERF`.
- **ABS**: Useful when handling negative values for clearer calculations.

### Summary:

The `ERF` function provides essential support for advanced statistical and engineering computations, specifically in
error analysis and probability distribution. Its integral-based calculations make it an important tool for professionals
in relevant disciplines.