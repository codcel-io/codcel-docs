<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ERF.PRECISE Function

The `ERF.PRECISE` function in Excel calculates the error function (ERF) with high precision. The error function is
commonly used in statistics and engineering to measure probabilities within the normal distribution and to evaluate
error rates.

This function works similarly to the `ERF` function but always calculates the integral of the error function between `0`
and a given value, with no option to specify an upper limit.

### Key Features of ERF.PRECISE:

- Returns the error function value from `0` to the provided **x** value with high precision.
- Ideal for statistical and engineering computations requiring accurate probabilities or error rate analysis.
- A simplified version of `ERF`, as it calculates the error function integral for a single limit only.

### Syntax:

```plaintext
ERF.PRECISE(x)
```

- **x**: The value up to which you want the error function calculated. This argument is required and must be numeric.

### Examples:

1. **Calculate the Precise Error Function for a Positive Value**:  
   `=ERF.PRECISE(1.5)`  
   Calculates the error function for values from `0` to `1.5`.  
   **Result**: `0.966105146`

2. **Calculate the Precise Error Function for a Negative Value**:  
   `=ERF.PRECISE(-1.5)`  
   Calculates the error function for values from `0` to `-1.5`.  
   **Result**: `-0.966105146`

3. **Calculate the Error Function for Zero**:  
   `=ERF.PRECISE(0)`  
   Calculates the error function for values from `0` to `0`.  
   **Result**: `0`

### Notes:

- The `ERF.PRECISE` function only accepts numeric input. Passing non-numeric values will result in a `#VALUE!` error.
- Like the `ERF` function, it is particularly suited for applications involving normal distribution, probability
  calculations, and error analysis.
- Since this function only computes the integral from `0` to `x`, it does not support specifying both lower and upper
  limits for integration.

### Applications:

- **Statistics**: Used for Gaussian (normal) distribution tables and advanced probability computations.
- **Signal Processing**: Helps measure error rates in communication systems with precise calculations.
- **Engineering**: Valuable for error and precision analysis in scientific and engineering projects.

### Related Functions:

- **ERF**: Computes the error function with optional lower and upper integration limits.  
  Example: `=ERF(1, 2)`
- **ERFC.PRECISE**: Computes the complementary error function (`1 - ERF(x)`) with enhanced precision.  
  Example: `=ERFC.PRECISE(1.5)`

### Summary:

The `ERF.PRECISE` function provides a simplified but highly precise implementation of the error function. Its integral
calculation is helpful in many scenarios involving statistics, probability, and engineering.