<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## POISSON.DIST Function

The `POISSON.DIST` function in Excel is used to **calculate the Poisson probability mass function or the cumulative
Poisson probability** for a given number of events. It is part of statistical analysis and helps in modeling the
probability of a certain number of events occurring within a given interval of time or space.

### Key Features of POISSON.DIST:

- **Discrete Probability Distribution**: Models the probability of independent events occurring in a fixed interval.
- **Modes of Operation**:
    - **Exact Probability** for a specific number of events.
    - **Cumulative Probability** for up to a specific number of events.
- **Applications in Statistics**: Often used in fields like quality control, traffic flow, and event prediction over
  time.

### Syntax:

```plaintext
POISSON.DIST(x, mean, cumulative)
```

- **x**: Required. The number of events (non-negative integer) for which to calculate the probability.
- **mean**: Required. The average number of events (λ) in the interval.
- **cumulative**: Required. A logical value that specifies the mode of calculation:
    - `TRUE` for the cumulative probability (P(X ≤ x)).
    - `FALSE` for the exact probability (P(X = x)).

### How It Works:

- **Exact Probability**:
  When `cumulative` is `FALSE`, the function uses the Poisson probability mass function:

  ```plaintext
  P(X = x) = (λ^x * e^(-λ)) / x!
  ```
  Where:
    - \( λ \) is the mean (expected number of events),
    - \( e \) is Euler’s number (≈ 2.718),
    - \( x! \) is the factorial of \( x \).

- **Cumulative Probability**:
  When `cumulative` is `TRUE`, the calculation is the sum of probabilities for all values from 0 to \( x \):

  ```plaintext
  P(X ≤ x) = Σ [(λ^i * e^(-λ)) / i!] for i = 0 to x
  ```

### Examples:

1. **Exact Probability of Events**:
   Calculate the probability of having exactly 5 events when the average number of events is 3:
   ```excel
   =POISSON.DIST(5, 3, FALSE)
   ```
   Result: `0.100818`

2. **Cumulative Probability**:
   Find the probability of having 3 or fewer events when the mean is 4:
   ```excel
   =POISSON.DIST(3, 4, TRUE)
   ```
   Result: `0.433470`

3. **Zero Events**:
   Probability of observing no events when the mean is 2.5:
   ```excel
   =POISSON.DIST(0, 2.5, FALSE)
   ```
   Result: `0.082085`

4. **Large Event Count**:
   Calculate the probability of exactly 15 events when the mean is 10:
   ```excel
   =POISSON.DIST(15, 10, FALSE)
   ```
   Result: `0.034718`

### Notes:

- **Valid Inputs**:
    - `x` must be a non-negative integer (values like 1.8 will truncate to 1).
    - `mean` must be a non-negative real number.
- If inputs are invalid, Excel returns an error:
    - `#VALUE!` for non-numeric inputs.
    - `#NUM!` for negative input values for `x` or `mean`.

- **Use Case**:
  The function is especially useful in scenarios involving rare and independent events, such as:
    - Predicting the number of system failures over time.
    - Estimating customer arrivals in a queue (e.g., a bank or service center).

- **Related Functions**:
    - `BINOM.DIST`: For binomial distributions.
    - `NORM.DIST`: For normal distributions.

### Applications:

- **Traffic Flow**: Forecasting the number of cars passing an intersection.
- **Healthcare**: Modeling the probability of a specific number of patient arrivals within a time period.
- **Biology**: Predicting the number of mutations in a DNA strand over a set interval.
- **System Design**: Analyzing event frequencies like server hits or system crashes.

> **Tip**: Use this function when the events occur randomly and their average rate is constant, with the assumption that
events happen independently of each other.