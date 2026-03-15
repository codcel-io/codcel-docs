<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## EXPON.DIST Function

The `EXPONDIST` (or `EXP.DIST` in newer versions of Excel) function calculates values for the **exponential distribution
**, which is a continuous probability distribution used to model the time between events in a Poisson process. It is
commonly used when analyzing queuing systems, reliability, and survival analysis.

The exponential distribution is widely applied in scenarios where occurrences are independent and happen at a constant
rate over time.

### Key Features of EXPON.DIST:

- Computes probabilities or cumulative probabilities for an exponential distribution.
- Models **time-dependent events**, e.g., time between arrivals of customers or failure of equipment.
- Can be used in both **probability density function (PDF)** and **cumulative distribution function (CDF)** modes.
- Enables predictive analysis based on the rate of event occurrence.

### Syntax:

```plaintext
EXPON.DIST(x, lambda, cumulative)
```

- **x**: The value of the random variable (non-negative). It represents the point in time or interval being analyzed.
- **lambda**: The rate parameter (positive), equivalent to the reciprocal of the mean (1/mean).
- **cumulative**: Logical value indicating whether to calculate the CDF or PDF of the exponential distribution:
    - `TRUE`: Returns the cumulative distribution function (CDF), giving the probability that the event occurs within
      the given interval.
    - `FALSE`: Returns the probability density function (PDF), evaluating the point probability density.

### Examples:

1. `=EXPON.DIST(2, 1.5, TRUE)`  
   Calculates the cumulative probability that the event occurs within 2 units of time, given a rate (`lambda`) of 1.5.  
   **Result**: A number between 0 and 1 (e.g., 0.9502).

2. `=EXPON.DIST(1, 2, FALSE)`  
   Computes the probability density at `x = 1` for an exponential distribution with `lambda = 2`.  
   **Result**: A positive number giving the point probability density (e.g., 0.2707).

3. `=EXPON.DIST(A1, 3.5, TRUE)`  
   Calculates the cumulative distribution for the value in cell `A1` with a rate of 3.5.  
   **Result**: A value representing the probability up to the given point.

### Notes:

- If `x` is negative, the function returns an error (`#NUM!`).
- If `lambda <= 0`, the function also returns an error (`#NUM!`).
- The result returned for `cumulative=TRUE` is calculated as:  
  **1 - EXP(-lambda * x)**  
  This gives the probability that the event happens within the given interval.
- When `cumulative=FALSE`, the function evaluates the PDF as:  
  **lambda * EXP(-lambda * x)**  
  This provides the point probability density for the time `x`.
- The function assumes the exponential distribution is appropriate for modeling time between independent random events.

> **Tip**: Use the `EXPONDIST` function in scenarios involving event intervals, such as predicting system downtime, time
to next arrival in queuing theory, or reliability analysis. The rate parameter (`lambda`) is crucial and should
represent the true rate of occurrences accurately for meaningful results.