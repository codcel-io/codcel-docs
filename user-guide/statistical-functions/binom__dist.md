<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BINOM.DIST Function

The `BINOM.DIST` function in Excel is used to calculate the **binomial probability distribution** for a given number of
successes in a set of independent trials. It is particularly useful for statistical analysis when dealing with
experiments or phenomena with binary outcomes (e.g., success/failure, true/false).

### Key Features of BINOM.DIST:

- Computes the probability of getting a specified number of successes over a defined number of independent trials.
- Allows for calculating either **exact probabilities** or **cumulative probabilities** up to a certain number of
  successes.
- Ideal for scenarios modeled by the binomial distribution, such as coin flips, quality testing, or event outcomes with
  fixed probabilities.

### Syntax:

```plaintext
BINOM.DIST(number_s, trials, probability_s, cumulative)
```

- **number_s**: The number of successes for which the probability is calculated. Must be a non-negative integer.
- **trials**: The total number of independent trials. Must be a positive integer.
- **probability_s**: The probability of success for an individual trial. Must be between `0` and `1`.
- **cumulative**: A logical value (`TRUE` or `FALSE`) that specifies whether to compute cumulative probabilities:
    - `TRUE`: Calculates the probability of getting up to and including `number_s` successes.
    - `FALSE`: Calculates the probability of getting exactly `number_s` successes.

### Examples:

1. `=BINOM.DIST(3, 10, 0.5, FALSE)`  
   Calculates the probability of exactly 3 successes in 10 trials, with a success probability of `0.5`.
   **Result**: `0.117188`.

2. `=BINOM.DIST(2, 5, 0.7, TRUE)`  
   Computes the cumulative probability of having at most 2 successes in 5 trials, where the success probability is
   `0.7`.
   **Result**: `0.16308`.

3. `=BINOM.DIST(4, 8, 0.25, FALSE)`  
   Calculates the exact probability of getting exactly 4 successes in 8 trials, with a success probability of `0.25`.
   **Result**: `0.033203`.

### Notes:

- If any input arguments fall outside their valid ranges (`number_s < 0`, `trials < 1`, or `probability_s` not between
  `0` and `1`), the function returns an error (`#NUM!` or `#VALUE!`).
- The trials are assumed to be independent, and the probability of success remains constant throughout all trials.
- In the case of cumulative probabilities (`cumulative = TRUE`), the function sums the probabilities of all outcomes up
  to and including `number_s` successes.

> **Tip**: Use `BINOM.DIST` for evaluating scenarios where the binomial distribution applies, such as assessing product
> reliability, testing proportions, or modeling binary experiments.