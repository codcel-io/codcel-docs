<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## EXPONDIST Function

The `EXPONDIST` function in Excel is used to calculate the value of the exponential distribution, which is typically
used to model the time between events in a process where events occur at a constant average rate. This function is
commonly applied in reliability testing, queuing theory, and other domains involving time-based probabilities.

### Key Features of EXPONDIST:

- Returns the **probability** or **cumulative probability** of the exponential distribution based on the rate of
  occurrence and a specified value.
- Can be used to calculate:
    - The **cumulative distribution function (CDF)** if cumulative is set to `TRUE`.
    - The **probability density function (PDF)** if cumulative is set to `FALSE`.
- Typically used in **failure rates**, **service times**, or **waiting times** analysis.

### Syntax:

```plaintext
EXPONDIST(x, lambda, cumulative)
```

- **x**: The value of the random variable. Must be greater than or equal to 0.
- **lambda**: The rate parameter of the distribution (i.e., the inverse of the mean). Must be greater than 0.
- **cumulative**: A logical value that determines the type of distribution returned:
    - If `TRUE`, the function returns the cumulative distribution function (CDF).
    - If `FALSE`, the function returns the probability density function (PDF).

### Example:

1. **Cumulative Distribution Function (CDF)**  
   `=EXPONDIST(2, 0.5, TRUE)`  
   Calculates the cumulative probability for `x = 2` with a rate parameter (`lambda`) of 0.5.  
   **Result**: 0.6321

2. **Probability Density Function (PDF)**  
   `=EXPONDIST(2, 0.5, FALSE)`  
   Computes the probability density for `x = 2` with a rate parameter (`lambda`) of 0.5.  
   **Result**: 0.1839

### Notes:

- **Cumulative Distribution Function (CDF)**:
    - Represents the probability that a random variable `X` is less than or equal to `x`.
    - Formula:
      ```plaintext
      F(x) = 1 - e^(-lambda * x)
      ```

- **Probability Density Function (PDF)**:
    - Represents the height of the probability distribution at `x`.
    - Formula:
      ```plaintext
      f(x) = lambda * e^(-lambda * x)
      ```

- **Non-Negative Values**:
    - The value of `x` must be non-negative (≥ 0). If `x < 0`, the function returns a `#NUM!` error.
    - The `lambda` parameter must also be positive (> 0), or else the function will return a `#NUM!` error.

### Formula Behind EXPONDIST:

The exponential distribution is defined as follows:

For the PDF:

```plaintext
f(x) = λ * e^(-λx) for x ≥ 0
```

For the CDF:

```plaintext
F(x) = P(X ≤ x) = 1 - e^(-λx) for x ≥ 0
```

Here:

- **x**: The value of interest.
- **λ (lambda)**: The rate parameter, which is the reciprocal of the mean (average time between events).

### Use Cases:

- **Reliability Testing**: Estimate the lifetime of components or systems.
- **Queue Management**: Model wait times in service systems (e.g., customer service).
- **Risk Assessment**: Model time between rare events (e.g., earthquakes, failures).

> **Tip**: For ease of interpretation, ensure units align consistently with the rate parameter (e.g., seconds, minutes,
> etc.) when applying this function.