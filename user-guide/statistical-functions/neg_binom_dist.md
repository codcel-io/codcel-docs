<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NEGBINOMDIST Function

The `NEGBINOMDIST` function in Excel is used to **calculate the negative binomial distribution**.  
This distribution gives the probability of a specified number of failures occurring before a certain number of successes
in a series of independent trials, where the probability of success in each trial is constant.

### Key Features of NEGBINOMDIST:

- Returns the probability of a specific number of failures before reaching a target number of successes.
- Useful in statistical models for scenarios such as defective product analysis or quality assurance.

### Syntax:

```plaintext
NEGBINOMDIST(number_f, number_s, probability_s)
```

- **number_f**: Required. The number of failures you want before reaching the desired number of successes.
- **number_s**: Required. The target number of successes.
- **probability_s**: Required. The probability of success in each trial (a decimal between 0 and 1).

### How It Works:

The function uses the **negative binomial probability formula**, which is based on the probability mass function for the
negative binomial distribution:

```plaintext
P(X = x) = COMBIN(x + r - 1, x) * (p ^ r) * ((1 - p) ^ x)
```

Where:

- `x` is the number of failures.
- `r` is the number of successes.
- `p` is the probability of a success.
- `COMBIN(n, k)` represents combinations.

### Examples:

1. **Basic Example**:
   Suppose you are conducting an experiment where the probability of success is `0.25` (25%), and you want to calculate
   the probability of getting 5 failures before 3 successes:
   ```excel
   =NEGBINOMDIST(5, 3, 0.25)
   ```
   Result: `0.055489`.

2. **In Product Testing**:
   If the probability of finding a defective product in testing is `0.1` (10%), and you are interested in the
   probability that you will find 7 defective items before identifying 4 functional products:
   ```excel
   =NEGBINOMDIST(7, 4, 0.9)
   ```

3. **Quality Control Scenario**:
   Calculate how likely it is to have `10` failures before achieving `8` successful production units, with a `60%`
   chance of success (probability = 0.6):
   ```excel
   =NEGBINOMDIST(10, 8, 0.6)
   ```

### Notes:

- **Input Validation**:
    - If `number_f` or `number_s` is non-numeric, the function returns `#VALUE!`.
    - If `probability_s` is less than 0 or greater than 1, the function returns `#NUM!`.

- **Behavior with Decimal Values**:
    - The function truncates non-integer values for **number_f** and **number_s** (e.g., `5.8` becomes `5`).

- **Probability Values**:
    - Ensure `probability_s` is a decimal between 0 and 1, representing a percentage likelihood (e.g., `0.75` for 75%).

### Applications:

- **Business and Quality Assurance**: Analyze the probability of failures in production before reaching a success
  milestone.
- **Gaming and Probability Models**: Model scenarios where a fixed number of successes are required in trials.
- **Statistics in Healthcare**: Use in models for occurrences of illness or recovery based on a treatment success
  probability.

> **Tip:** The `NEGBINOMDIST` function was replaced by the `NEGBINOM.DIST` function in Excel 2010 and beyond, which
supports additional features for cumulative probabilities.