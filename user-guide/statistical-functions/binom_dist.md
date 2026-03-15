<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## BINOMDIST Function

The `BINOMDIST` function in Excel calculates the **individual term binomial probability** for a given number of
successes in a set of trials, based on the probability of a single success. In other words, it computes the probability
of achieving a specified number of successes in a fixed number of independent trials with the same probability of
success.

This function is helpful in statistical analyses, especially in scenarios involving binary outcomes (e.g.,
success/failure, true/false).

### Key Features of BINOMDIST:

- Evaluates the binomial distribution's probability for a specific number of successes.
- Can calculate either **exact probabilities** or **cumulative probabilities** up to a specified number of successes.

### Syntax:

```plaintext
BINOMDIST(number_s, trials, probability_s, cumulative)
```

- **number_s**: The number of successes for which you want to calculate the probability. Must be a non-negative integer.
- **trials**: The total number of independent trials. Must be a positive integer.
- **probability_s**: The probability of success for each trial. Must be between `0` and `1`.
- **cumulative**: A logical value (`TRUE` or `FALSE`) that specifies whether to calculate cumulative probabilities:
    - If `TRUE`, `BINOMDIST` computes the probability of having at most `number_s` successes.
    - If `FALSE`, it computes the probability of exactly `number_s` successes.

### Examples:

1. `=BINOMDIST(3, 10, 0.5, FALSE)`  
   Calculates the probability of exactly 3 successes out of 10 trials, where the probability of success is `0.5`.
   **Result**: `0.1171875`.

2. `=BINOMDIST(2, 5, 0.7, TRUE)`  
   Computes the cumulative probability of having at most 2 successes out of 5 trials, with a success probability of
   `0.7`.
   **Result**: `0.16308`.

3. `=BINOMDIST(4, 8, 0.25, FALSE)`  
   Calculates the probability of exactly 4 successes out of 8 trials, with a success probability of `0.25`.
   **Result**: `0.033203`.

### Notes:

- If any of the arguments are outside their valid ranges (`number_s < 0`, `trials < 1`, `probability_s` not between `0`
  and `1`), the function returns an error (`#NUM!` or `#VALUE!`).
- The `BINOMDIST` function assumes each trial is independent and that the probability of success remains constant across
  trials.
- For cumulative probability calculations, the sum of all probabilities up to `number_s` is returned.

> **Tip**: Use `BINOMDIST` for experiments modeled by the binomial distribution, such as quality control, flipping a
> coin, or testing pass rates.