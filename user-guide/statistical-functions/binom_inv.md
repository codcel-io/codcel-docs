<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BINOM.INV Function

The `BINOM.INV` function in Excel calculates the **smallest value for which the cumulative binomial distribution is
greater than or equal to a given criterion or probability**. In other words, it finds the **inverse** of the binomial
cumulative distribution.

This function is helpful when you need to determine the minimum number of successes required to meet or exceed a target
cumulative probability in statistical analyses involving binary outcomes (e.g., success/failure).

### Key Features of BINOM.INV:

- Determines the smallest number of successes for which the cumulative probability reaches or exceeds a specified
  threshold.
- Inverse operation of cumulative binomial probability.

### Syntax:

```plaintext
BINOM.INV(trials, probability_s, alpha)
```

- **trials**: The total number of independent trials. Must be a positive integer.
- **probability_s**: The probability of success on each trial. Must be a number between `0` and `1`.
- **alpha**: The target cumulative probability. Must be a number between `0` and `1`.

### Examples:

1. `=BINOM.INV(10, 0.5, 0.8)`  
   Calculates the smallest number of successes required in 10 trials, where the probability of success for each trial is
   `0.5`, so that the cumulative probability is at least `0.8`.  
   **Result**: `6`.

2. `=BINOM.INV(15, 0.3, 0.5)`  
   Finds the smallest number of successes in a series of 15 trials, each with a success probability of `0.3`, to reach a
   cumulative probability of `0.5`.  
   **Result**: `5`.

3. `=BINOM.INV(8, 0.6, 0.9)`  
   Determines the minimum number of successes required in 8 trials with a success probability of `0.6` to meet a
   cumulative probability of `0.9`.  
   **Result**: `6`.

### Notes:

- If any of the arguments are outside their valid ranges (`trials < 1`, `probability_s` not between `0` and `1`, `alpha`
  not between `0` and `1`), the function returns an error (`#NUM!` or `#VALUE!`).
- The function assumes trials are independent, and the probability of success is constant across all trials.
- `BINOM.INV` is particularly useful for modeling processes or experiments using the binomial distribution, such as
  reliability testing, quality control, and risk analysis.

> **Tip**: Use `BINOM.INV` to back-calculate the required number of successes for meeting a specific target probability.