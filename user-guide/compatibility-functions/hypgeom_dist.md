<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## HYPGEOMDIST Function

The `HYPGEOMDIST` function in Excel is used to calculate the **hypergeometric distribution**, which determines the
probability of a certain number of successes in a fixed number of draws, without replacement, from a finite population.
This function is equivalent to the modern `HYPGEOM.DIST` but was used in earlier versions of Excel.

### Key Features of HYPGEOMDIST:

- Computes the probability of obtaining a specific number of successes in a sample.
- Assumes sampling without replacement, making it suitable for scenarios such as card games or quality control.
- Always calculates the **probability mass function (PMF)**, as it does not support cumulative probabilities like
  `HYPGEOM.DIST`.

### Syntax:

```plaintext
HYPGEOMDIST(sample_s, number_sample, population_s, number_population)
```

- **sample_s**: The number of successes in the sample (integer).
- **number_sample**: The size of the sample or the number of draws (integer).
- **population_s**: The total number of successes in the population (integer).
- **number_population**: The size of the overall population (integer).

### Example:

1. **Calculating PMF (Probability for Exact Number of Successes)**  
   Suppose you are drawing cards from a deck of 52 cards:
    - You draw **5 cards**.
    - You want to calculate the probability of getting exactly **2 aces** when there are **4 aces** in the deck.  
      Formula:  
      `=HYPGEOMDIST(2, 5, 4, 52)`  
      **Result**: Probability of getting exactly 2 aces in the 5-card sample.

### Notes:

- The `HYPGEOMDIST` function assumes sampling **without replacement**, meaning each draw reduces the size of the
  population.
- **Output**:
    - Returns a probability value between **0 and 1**.
    - A `#NUM!` error is displayed if the arguments are invalid (e.g., if sample size exceeds the population size).
- **Invalid inputs**:
    - Non-integer or negative values for **sample_s**, **number_sample**, **population_s**, or **number_population**
      will result in errors.

### Use Cases:

- **Quality Control**: Determine the probability of defective items in a random sample taken from a batch.
- **Games and Probability**: Calculate probabilities in card games or similar finite scenarios.

> **Note**: The `HYPGEOMDIST` function has been replaced by `HYPGEOM.DIST` in newer versions of Excel, which provides
> both PMF and CDF options. Consider using `HYPGEOM.DIST` for a more versatile function in those versions.