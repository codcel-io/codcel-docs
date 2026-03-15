<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## HYPGEOM.DIST Function

The `HYPGEOM.DIST` function in Excel is used to calculate the **hypergeometric distribution**, which is a discrete
probability distribution related to sampling without replacement from a finite population. It is particularly helpful in
probability and statistics for determining the likelihood of a specific outcome in a sample.

### Key Features of HYPGEOM.DIST:

- Computes the probability of obtaining a specific number of successes (sample successes) from a population.
- Useful for statistical analysis involving populations, for example, in quality control, genetics, or card games where
  sampling occurs without replacement.
- Can return probabilities for both cumulative and exact distributions depending on the input.

### Syntax:

```plaintext
HYPGEOM.DIST(sample_s, number_sample, population_s, number_pop, cumulative)
```

- **sample_s**: The number of successes in the sample (required).
- **number_sample**: The size of the sample drawn from the population (required).
- **population_s**: The total number of successes in the population (required).
- **number_pop**: The size of the entire population (required).
- **cumulative**: A logical value (TRUE or FALSE) that determines the type of distribution to return (required):
    - `TRUE` returns the cumulative probability (`P(X ≤ sample_s)`).
    - `FALSE` returns the exact probability (`P(X = sample_s)`).

### How It Works:

The formula for the hypergeometric distribution is:

```plaintext
HYPGEOM.DIST = [ (C(population_s, sample_s) * C(failures, number_sample - sample_s)) ] / C(number_pop, number_sample)
```

Where:

- `C(a, b)` is the combination function (`a! / (b! * (a - b)!)`).
- `failures` = `number_pop - population_s`.

### Examples:

1. **Exact Probability Calculation**:

   Suppose you have a deck of cards (52 cards in total) with 13 hearts, and you draw 5 cards at random. The probability
   of getting exactly 2 hearts is:

   ```excel
   =HYPGEOM.DIST(2, 5, 13, 52, FALSE)
   ```
   Result: `0.325`.

2. **Cumulative Probability Calculation**:

   For the same scenario, if you want to calculate the probability of getting 2 or fewer hearts:

   ```excel
   =HYPGEOM.DIST(2, 5, 13, 52, TRUE)
   ```
   Result: `0.816`.

3. **Quality Control Example**:

   A factory produces 1,000 widgets, 200 of which are defective. If a quality inspector selects 10 widgets at random,
   the probability of finding exactly 3 defective widgets can be calculated as:

   ```excel
   =HYPGEOM.DIST(3, 10, 200, 1000, FALSE)
   ```

4. **Using Cumulative in Quality Control**:

   The probability of finding 3 or fewer defective widgets in the same scenario is:

   ```excel
   =HYPGEOM.DIST(3, 10, 200, 1000, TRUE)
   ```

### Notes:

- **Parameter Constraints**:
    - Ensure that all numeric inputs are non-negative integers.
    - The `sample_s`, `population_s`, and `number_sample` must not exceed `number_pop`.
- Setting the `cumulative` argument to `TRUE` calculates the cumulative probability up to and including the specified
  `sample_s`.

### Applications:

- **Quality Control**: Estimating the probability of defective items in a sample drawn from a production batch.
- **Card Games**: Predicting probabilities of drawing specific cards in hands.
- **Genetics Studies**: Calculating probabilities in population traits based on known distributions.
- **Statistical Analysis**: Sampling studies or experiments with finite populations without replacement.

> **Tip:** Use the `HYPGEOM.DIST` function for problems involving finite populations where items are not replaced after
> sampling. This function complements other probability functions like `BINOM.DIST` (binomial distribution, for sampling
> with replacement).