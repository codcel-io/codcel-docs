<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CRITBINOM Function

The `CRITBINOM` function in Excel is used to determine the smallest value (called the critical value) for which the
cumulative binomial distribution is greater than or equal to a given criterion. This function is commonly used in
probability and statistical analysis to find thresholds for binomial outcomes.

### Key Features of CRITBINOM:

- Returns the **inverse of the cumulative binomial distribution** for a specified number of trials, probability of
  success, and criterion value.
- Useful in determining **critical thresholds** or benchmarks for binomial experiments.
- Often applied in **quality control**, **hypothesis testing**, and other areas where binomial probabilities are
  relevant.

### Syntax:

```plaintext
CRITBINOM(trials, probability_s, alpha)
```

- **trials**: The total number of independent trials. Must be a positive integer.
- **probability_s**: The probability of success on a single trial. Must be a value between 0 and 1.
- **alpha**: The desired cumulative probability (criterion value). Must be a value between 0 and 1.

### Example:

1. `=CRITBINOM(10, 0.5, 0.8)`  
   Returns the smallest number of successes in 10 trials (each with a probability of success of 50%) such that the
   cumulative probability is at least 0.8.  
   **Result**: 6

2. `=CRITBINOM(20, 0.3, 0.4)`  
   Calculates the critical value for 20 trials with a success probability of 30%, where the cumulative probability
   reaches 40%.  
   **Result**: 5 (or the equivalent smallest number of successes).

### Notes:

- **Cumulative Threshold**: The function calculates the point at which the cumulative binomial probability meets or
  exceeds the provided `alpha`.
- **Non-negative Values**: The result will always be a non-negative integer.
- **Probability Range**: If `probability_s` or `alpha` is outside the range of 0 to 1, the function will return a
  `#NUM!` error.
- **Trial Count**: If `trials` is not a positive integer, the function will return a `#VALUE!` error or incorrect
  results.

### Formula Behind CRITBINOM:

Mathematically, the cumulative probability for binomial distribution is given by:

```plaintext
P(X <= k) = Σ [C(n, i) * p^i * (1-p)^(n-i)] for i = 0 to k
```

Where:

- **n**: Number of trials.
- **p**: Probability of success on a single trial.
- **k**: The critical value or observed successes.
- **C(n, i)**: The binomial coefficient.

The `CRITBINOM` function finds the smallest `k` such that:

```plaintext
P(X <= k) ≥ alpha
```

### Use Cases:

- **Quality Control**: Determine the minimum successes needed in a batch inspection to accept a product.
- **Risk Assessment**: Define thresholds for safety or acceptance limits in experiments or trials.
- **Probability Analysis**: Set critical thresholds for hypothesis testing involving binomial probabilities.

> **Tip**: For advanced statistical applications, consider using newer functions like `BINOM.INV` in modern Excel
> versions, as they are more robust and flexible for similar calculations.