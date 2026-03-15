<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PROB Function

The `PROB` function in Excel is used to **calculate the probability associated with a range of values between upper and
lower limits**, given a set of corresponding probabilities. This is particularly useful in statistical analysis for
calculating the likelihood of a certain value range occurring based on a probability distribution.

### Key Features of PROB:

- **Probability Analysis**: Computes the probability that a random variable lies within a specified range.
- **Supports Discrete Distributions**: Uses explicit probabilities provided for each value.
- **Flexible Range Boundaries**: Allows specification of upper and lower bounds to calculate cumulative probabilities.

### Syntax:

```plaintext
PROB(x_range, prob_range, lower_limit, [upper_limit])
```

- **x_range**: Required. An array or range of numerical data values (e.g., possible outcomes).
- **prob_range**: Required. An array or range of probabilities corresponding to the values in `x_range`. The total of
  these probabilities must be equal to 1.
- **lower_limit**: Required. The lower boundary for the range of values to calculate the cumulative probability.
- **upper_limit**: Optional. The upper boundary for the range of values to calculate the cumulative probability. If
  omitted, the function returns the probability associated with the `lower_limit` alone.

### How It Works:

- `PROB` sums the probabilities of all values in `x_range` that fall between `lower_limit` and `upper_limit` (
  inclusive).
- If `upper_limit` is omitted, it simply returns the probability associated with the `lower_limit`.

### Examples:

1. **Single Value Probability**:
   To calculate the probability of exactly 10 occurring, where the probabilities of outcomes are defined:
   ```excel
   =PROB({5, 10, 15}, {0.2, 0.5, 0.3}, 10)
   ```
   Result: `0.5`

2. **Range of Values**:
   Find the probability of a value between 5 and 15 (inclusive):
   ```excel
   =PROB({5, 10, 15}, {0.2, 0.5, 0.3}, 5, 15)
   ```
   Result: `1.0` (Sum of probabilities: `0.2 + 0.5 + 0.3`)

3. **Cumulative Probability**:
   Calculate the probability of a value less than or equal to 10:
   ```excel
   =PROB({5, 10, 15}, {0.2, 0.5, 0.3}, 5, 10)
   ```
   Result: `0.7` (Sum of probabilities: `0.2 + 0.5`)

### Notes:

- **Valid Inputs**:
    - The lengths of `x_range` and `prob_range` must match.
    - The sum of values in `prob_range` must equal 1 (or close to 1 due to rounding errors).
    - If `lower_limit` or `upper_limit` is outside the range of values in `x_range`, the function returns `0`.

- **Error Conditions**:
    - `#NUM!` if the sum of probabilities in `prob_range` is not 1.
    - `#VALUE!` if non-numeric values are passed to any argument.

- **Use Case**:
  This function is particularly useful in scenarios requiring custom probability distributions, such as:
    - Predicting the likelihood of certain scores or outcomes in statistical simulations.
    - Evaluating the probability of specific grades being achieved in a test scenario.

### Applications:

- **Education**: Assessment score likelihood based on distributions.
- **Risk Analysis**: Calculating probabilities for value ranges in custom risk models.
- **Financial Modeling**: Probability of returns for specific portfolio outcomes.
- **Manufacturing**: Evaluating product defect probabilities within given ranges.

> **Tip**: Always ensure `prob_range` represents a valid probability distribution with a total sum of 1 before using the
function.