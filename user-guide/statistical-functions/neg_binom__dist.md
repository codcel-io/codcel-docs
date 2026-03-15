<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NEGBINOM.DIST Function

The `NEGBINOM.DIST` function in Excel is used to **calculate the negative binomial distribution**, which represents the
probability of a certain number of failures occurring before a specified number of successes is achieved in a series of
independent trials.

### Key Features of NEGBINOM.DIST:

- Useful in scenarios where you want to model the number of failures before achieving a certain number of successes (
  e.g., defective items before reaching a certain count of good items in batch testing).
- Can compute either the probability mass function (PMF) or cumulative distribution function (CDF).

### Syntax:

```plaintext
NEGBINOM.DIST(number_f, number_s, probability_s, cumulative)
```

#### Parameters:

1. **number_f**: Required. The number of failures before the specified number of successes. Must be an integer ≥ 0.
2. **number_s**: Required. The number of successes that need to be achieved. Must be an integer > 0.
3. **probability_s**: Required. The probability of a success in an individual trial. A decimal value between 0 and 1.
4. **cumulative**: Required. A logical value (TRUE or FALSE) that specifies the type of distribution to calculate:
    - **TRUE** = Returns the cumulative distribution function (probability of up to `number_f` failures).
    - **FALSE** = Returns the probability mass function (probability of exactly `number_f` failures).

### How It Works:

1. The function calculates the probability using the negative binomial distribution formula.
2. Depending on the `cumulative` parameter:
    - If `FALSE`, it provides the exact probability of seeing that specific number of failures.
    - If `TRUE`, it calculates the cumulative probability up to and including the given number of failures.

### Examples:

1. **Exact Probability of Failures (PMF)**:
   To calculate the probability of exactly 3 failures before achieving 5 successes when the success probability is 70%:
   ```excel
   =NEGBINOM.DIST(3, 5, 0.7, FALSE)
   ```
   Result: The PMF value for the specified parameters.

2. **Cumulative Probability of Failures (CDF)**:
   To calculate the cumulative probability of up to 3 failures before 5 successes:
   ```excel
   =NEGBINOM.DIST(3, 5, 0.7, TRUE)
   ```
   Result: The CDF value with the given inputs.

3. **Using Higher Failure Counts**:
   For 10 failures before achieving 8 successes with a success probability of 40%:
   ```excel
   =NEGBINOM.DIST(10, 8, 0.4, FALSE)
   ```
   Result: The exact probability of 10 failures.

### Notes:

- **Ranges for Input Values**:
    - If `number_f` or `number_s` are non-integers, they are truncated to integers.
    - Any invalid input (e.g., `number_f < 0`, `number_s <= 0`, or `probability_s` not in range [0, 1]) results in the
      `#NUM!` error.

- **Practical Applications**:
    - **Quality Control**: Model defective parts before finding a specific count of non-defective ones.
    - **Business Analysis**: Calculate the likelihood of failures in customer interactions before achieving a number of
      successful outcomes.
    - **Risk Management**: Assess probabilities in repeated trials where multiple failures are acceptable before
      successes are reached.

- **Relation to Statistical Theory**:
    - The function assumes trials are **independent**.
    - It complements other Excel distribution functions, such as `BINOM.DIST` for related use cases.

### Applications:

- **Statistical Modeling**: Analyze the probability of a fixed number of failures before a specific number of successes.
- **Experimentation**: Understand outcomes in repeated trials where success has a fixed probability.
- **Forecasting**: Simulate scenarios involving repeated attempts to achieve a target result.

> **Tip:** Use **cumulative mode** (`cumulative = TRUE`) for calculating probabilities across a range of outcomes.