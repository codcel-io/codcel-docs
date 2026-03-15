<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ERFC Function

The `ERFC` function in Excel calculates the complementary error function, which is equal to `1 - ERF(x)`. This function
is commonly used in probability, statistics, and engineering applications to compute complementary probabilities and
error rates.

### Key Features of ERFC:

- Returns the complement of the error function, which represents the probability of the result being outside the given
  range in the normal distribution.
- Can handle both positive and negative values of **x**.
- Useful for calculations involving tail probabilities in statistics.

### Syntax:

```plaintext
ERFC(x)
```

- **x**: The value for which the complementary error function is to be calculated. This argument is required and must be
  numeric.

### Examples:

1. **Calculate the Complementary Error Function for a Positive Value**:  
   `=ERFC(1)`  
   Calculates `1 - ERF(1)`.  
   **Result**: `0.157299207`

2. **Calculate the Complementary Error Function for a Negative Value**:  
   `=ERFC(-1)`  
   Calculates `1 - ERF(-1)`.  
   **Result**: `1.842700793`

3. **Calculate the Complementary Error Function for Zero**:  
   `=ERFC(0)`  
   Calculates `1 - ERF(0)`.  
   **Result**: `1`

### Notes:

- The `ERFC` function requires **x** to be numeric. Non-numeric inputs will result in a `#VALUE!` error.
- The function is designed to compute the probability that a random variable in a standard normal distribution lies
  outside the specified range.
- `ERFC` is particularly suited for statistical computation, reliability analysis, and some engineering applications.

### Applications:

- **Statistics**: Useful for calculating tail probabilities in normal distributions.
- **Engineering**: Often used in signal processing to analyze communication error rates.
- **Probability Theory**: Helpful in scenarios where complementary outcomes are of interest.

### Related Functions:

- **ERF**: Computes the error function, providing the probability within a specified range.  
  Example: `=ERF(1.5)`
- **ERFC.PRECISE**: Computes the complementary error function with enhanced precision for better accuracy.  
  Example: `=ERFC.PRECISE(1.5)`

### Summary:

The `ERFC` function provides a convenient way to calculate the complementary error function. It is widely used in
probability, statistics, and engineering, making it an essential tool for applications requiring the evaluation of tail
probabilities and error rates.