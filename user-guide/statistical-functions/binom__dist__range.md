<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BINOM.DIST.RANGE Function

The `BINOM.DIST.RANGE` function in Excel calculates the probability of a **specific range of successes** in a binomial
distribution. It is a more flexible version of the binomial distribution functions since it allows users to compute
probabilities over a range of successes rather than a single value or cumulative probabilities.

This function is particularly useful in scenarios involving binary outcomes (e.g., success/failure, yes/no) where you
are interested in the probability of achieving successes within a specified range.

### Key Features of BINOM.DIST.RANGE:

- Computes the probability of having between a specified minimum and maximum number of successes (both inclusive) in a
  fixed number of independent trials.
- Useful when a range of outcomes is of interest, rather than a specific value or cumulative probability.

### Syntax:

```plaintext
BINOM.DIST.RANGE(trials, probability_s, number_s, [number_s2])
```

- **trials**: The total number of independent trials. Must be a positive integer.
- **probability_s**: The probability of success for each trial, expressed as a decimal. Must be between `0` and `1`.
- **number_s**: The minimum number of successes in the range for which you want to calculate the probability. Must be a
  non-negative integer.
- **[number_s2]**: *(Optional)* The maximum number of successes in the range. If omitted, the function calculates the
  probability of exactly `number_s` successes.

### Examples:

1. `=BINOM.DIST.RANGE(10, 0.5, 3)`  
   Calculates the probability of exactly 3 successes out of 10 trials, where the probability of success is `0.5`.  
   **Result**: `0.1171875`.

2. `=BINOM.DIST.RANGE(10, 0.5, 3, 5)`  
   Calculates the probability of having between 3 and 5 successes (inclusive) out of 10 trials, where the probability of
   success is `0.5`.  
   **Result**: `0.623046875`.

3. `=BINOM.DIST.RANGE(8, 0.3, 2, 4)`  
   Computes the probability of having between 2 and 4 successes out of 8 trials, where the success probability is
   `0.3`.  
   **Result**: `0.524682624`.

### Notes:

- If any arguments are outside their valid ranges (`trials < 1`, `probability_s` not between `0` and `1`, or `number_s`
  and `number_s2` not integers or outside the range of `0` to `trials`), the function returns an error (`#NUM!` or
  `#VALUE!`).
- If `[number_s2]` is omitted, the function behaves like a standard binomial probability calculation for an exact number
  of successes.
- The `BINOM.DIST.RANGE` function assumes that each trial is independent and that the probability of success remains
  consistent across trials.
- The function is particularly powerful for probability computations over ranges, which makes it ideal for modeling
  experiments where success within certain thresholds is desired.

> **Tip**: Use `BINOM.DIST.RANGE` for scenarios where you need to model a range of outcomes in experiments, such as
> analyzing quality control defects, predicting pass outcomes in exams, or measuring thresholds in surveys.