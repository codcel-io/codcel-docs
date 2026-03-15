<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHISQ.TEST Function

The `CHISQ.TEST` function in Excel is used to compute the **probability of observing a Chi-Square statistic** as extreme
as, or more extreme than, the one computed from the given data. This function is widely used in statistical hypothesis
testing, particularly for **Chi-Square tests of independence** or **goodness-of-fit tests**.

It measures how the **expected values** compare to the **observed values** in categorical data, providing a **p-value**
that indicates the likelihood of obtaining such a result by chance.

### Key Features of CHISQ.TEST:

- **Calculates the p-value** for a Chi-Square test, enabling users to reject or fail to reject the null hypothesis.
- Useful for comparing observed and expected frequencies in categorical datasets.
- Commonly employed in tests of:
    - Independence between two categorical variables.
    - Goodness-of-fit for observed data to a theoretical distribution.

### Syntax:

```plaintext
CHISQ.TEST(actual_range, expected_range)
```

- **actual_range**: The range containing the observed (actual) frequencies. Must have the same dimensions as
  `expected_range`.
- **expected_range**: The range containing the expected frequencies. Must have the same dimensions as `actual_range`.

### Examples:

1. **Chi-Square Test for Independence**

   Assume you have the following data for observed (actual) frequencies:

   | Category A | Category B |
      |------------|------------|
   | 20         | 30         |
   | 25         | 35         |

   And the expected frequencies:

   | Category A | Category B |
      |------------|------------|
   | 22.5       | 27.5       |
   | 22.5       | 32.5       |

   Using the formula:

   ```excel
   =CHISQ.TEST(A1:B2, A3:B4)
   ```

   **Result**: Returns the p-value of the Chi-Square test.

2. **Goodness-of-Fit Test**

   Observed data: `{18, 22, 40}`  
   Expected data: `{20, 20, 40}`

   Using the formula:

   ```excel
   =CHISQ.TEST({18,22,40}, {20,20,40})
   ```

   **Result**: Returns the probability of observing the given Chi-Square statistic under the null hypothesis.

### Notes:

- The `CHISQ.TEST` function is essential for hypothesis testing involving categorical data.
- If `actual_range` or `expected_range` have different dimensions, the function will return an error (`#N/A`).
- For small sample sizes, the Chi-Square test may not be valid; ensure the expected frequencies are sufficiently large (
  typically ≥5).
- A small p-value (e.g., <0.05) indicates strong evidence against the null hypothesis, suggesting that the observed and
  expected frequencies are significantly different.

> **Tip**: Use `CHISQ.TEST` as part of a broader analysis context to evaluate hypothesis tests for independence or
> goodness-of-fit. Always pair results with domain expertise and the specific context of your dataset.