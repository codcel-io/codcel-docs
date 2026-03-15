<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ERFC.PRECISE Function

The `ERFC.PRECISE` function in Excel calculates the complementary error function (ERFC) with high precision. The
complementary error function is defined as `1 - ERF(x)`, where `ERF` is the error function. It is commonly used in
statistics, probability calculations, and engineering to measure tail probabilities or error rates.

This function works similarly to the `ERFC` function but ensures calculation precision for the specified input.

### Key Features of ERFC.PRECISE:

- Returns the complementary error function value (`1 - ERF(x)`) for a given **x** with high precision.
- Useful for statistical and engineering computations requiring accurate measurements of tail probabilities or errors.
- Requires only one input — the value of **x**.

### Syntax:

```plaintext
ERFC.PRECISE(x)
```

- **x**: The value for which you want the complementary error function calculated. This argument is required and must be
  numeric.

### Examples:

1. **Calculate the Complementary Error Function for a Positive Value**:  
   `=ERFC.PRECISE(1.5)`  
   Calculates `1 - ERF(1.5)`.  
   **Result**: `0.033894854`

2. **Calculate the Complementary Error Function for a Negative Value**:  
   `=ERFC.PRECISE(-1.5)`  
   Calculates `1 - ERF(-1.5)`.  
   **Result**: `1.966105146`

3. **Calculate the Complementary Error Function for Zero**:  
   `=ERFC.PRECISE(0)`  
   Calculates `1 - ERF(0)`.  
   **Result**: `1`

### Notes:

- The `ERFC.PRECISE` function only accepts numeric input. Passing non-numeric values will result in a `#VALUE!` error.
- It is a precise and simplified implementation of the complementary error function.
- Primary use cases include areas where accurate calculation of tail probabilities or cumulative distributions is
  critical.

### Applications:

- **Statistics**: Used for calculating probabilities in the tail regions of Gaussian (normal) distribution.
- **Engineering**: Valuable for analyzing error rates in communication systems with precise computations.
- **Probability**: Helpful in cumulative probability functions and advanced signal processing tasks.

### Related Functions:

- **ERF.PRECISE**: Computes the error function integral (`ERF(x)`) from `0` to a specified `x` with high precision.  
  Example: `=ERF.PRECISE(1.5)`
- **ERFC**: Computes the complementary error function but does not guarantee high precision.  
  Example: `=ERFC(1.5)`

### Summary:

The `ERFC.PRECISE` function provides a precise calculation for the complementary error function. It is particularly
suited for applications in statistics, probability, and engineering, where precision and simplicity are essential in
handling error rates and tail probabilities.