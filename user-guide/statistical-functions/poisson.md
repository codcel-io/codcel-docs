<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## POISSON Function

The `POISSON` function in Excel is used to **calculate the Poisson probability mass function or the cumulative Poisson
probability** for a given number of events. The Poisson distribution is commonly applied to model the number of times an
event occurs within a fixed interval of time or space.

### Key Features of POISSON:

- **Discrete Probability**: Computes probabilities for discrete events occurring in a fixed interval.
- **Two Modes**: Can calculate the probability for an exact number of events or the cumulative probability up to a
  specified number.
- **Useful in Statistics and Probability**: Frequently used in areas like quality control, traffic flow analysis, and
  system reliability.
- **Flexibility**: Accepts non-integer values for the mean (λ), but the event count (x) must be a non-negative integer.

### Syntax:

```plaintext
POISSON(x, mean, cumulative)
```

- **x**: Required. The number of events (non-negative integer) for which to calculate the probability.
- **mean**: Required. The expected number of events (λ) within the interval.
- **cumulative**: Required. A logical value that specifies the type of probability calculation:
    - `TRUE` for the cumulative probability (P(X ≤ x)).
    - `FALSE` for the exact probability (P(X = x)).

### How It Works:

- **Exact Probability**:
  When `cumulative` is `FALSE`, the `POISSON` function calculates the probability for exactly `x` events using the
  formula:

  ```plaintext
  P(X = x) = (λ^x * e^(-λ)) / x!
  ```
  Where:
    - \( λ \) is the mean (expected number of events),
    - \( e \) is the base of the natural logarithm,
    - \( x! \) is the factorial of \( x \).

- **Cumulative Probability**:
  When `cumulative` is `TRUE`, the function calculates the cumulative probability using the formula:

  ```plaintext
  P(X ≤ x) = Σ [(λ^i * e^(-λ)) / i!] for i = 0 to x
  ```

### Examples:

1. **Exact Probability**:
   Calculate the probability of observing exactly 3 events when the expected number of events is 2:
   ```excel
   =POISSON(3, 2, FALSE)
   ```
   Result: `0.180447`

2. **Cumulative Probability**:
   Calculate the probability of observing 3 or fewer events when the expected number of events is 2:
   ```excel
   =POISSON(3, 2, TRUE)
   ```
   Result: `0.857123`

3. **No Events**:
   To calculate the probability of observing no events when the expected value is 1.5:
   ```excel
   =POISSON(0, 1.5, FALSE)
   ```
   Result: `0.223130`

4. **High Mean Value**:
   Calculate the probability of exactly 10 occurrences when the mean is 12:
   ```excel
   =POISSON(10, 12, FALSE)
   ```
   Result: `0.104837`

### Notes:

- **Input Restrictions**:
    - `x` must be a non-negative integer. If `x` is not an integer, Excel will truncate it to an integer.
    - `mean` must be a non-negative numeric value.
    - If any of the inputs are invalid, Excel returns the `#VALUE!` error.

- **Use Case**:
    - Use the `POISSON` function to evaluate probabilities where events happen at a constant rate, with the assumption
      that events are independent of one another.

- **Complementary Functions**:
    - The `BINOM.DIST` function is related but applies to **binomial distributions**, where the number of total
      outcomes (n) is fixed and independent trials are considered.

### Applications:

- **Queue Management**: Analyze the number of service requests arriving at a call center.
- **Risk Analysis**: Estimate the number of accidents or failures in a manufacturing process.
- **Traffic Modeling**: Predict the number of cars passing through an intersection within a specific time frame.
- **Biology**: Model the distribution of mutations in DNA over given sequences.

> **Tip**: The function is essential for analyzing rare or random events within fixed scales of measurement, such as
> time, distance, area, etc.