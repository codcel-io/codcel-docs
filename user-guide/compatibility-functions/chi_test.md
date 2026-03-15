<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CHITEST Function

The `CHITEST` function in Excel returns the probability associated with the chi-squared statistic for a data set. It is
often used to test the independence of two variables in a contingency table or to evaluate the goodness-of-fit between
observed and expected frequencies.

### Key Features of CHITEST:

- Calculates the **p-value** for the chi-squared test.
- Helps determine whether the observed data differs significantly from the expected data under the null hypothesis.
- Commonly used in **statistical hypothesis testing** for:
    - **Goodness-of-fit tests**.
    - **Independence tests** for categorical data.

### Syntax:

```plaintext
CHITEST(actual_range, expected_range)
```

- **actual_range**: The range of observed values (must be numeric and of the same dimensions as `expected_range`).
- **expected_range**: The range of expected values corresponding to `actual_range`.

### Examples:

1. `=CHITEST(A1:A5, B1:B5)`  
   Returns the p-value for the chi-squared test based on the observed values in the range `A1:A5` and the corresponding
   expected values in `B1:B5`.  
   **Result**: P-value indicating the likelihood that the differences occurred by chance.

2. `=CHITEST({10, 20, 30}, {11, 19, 30})`  
   Calculates the p-value for observed values `{10, 20, 30}` and expected values `{11, 19, 30}`.  
   **Result**: A value between 0 and 1 representing the probability.

### Notes:

- A **low p-value** (e.g., less than 0.05) indicates that you should reject the null hypothesis, suggesting that the
  observed data significantly differs from the expected data.
- The `actual_range` and `expected_range` must have the same dimensions; otherwise, Excel returns a `#N/A` error.
- Values in `expected_range` must all be greater than 0; otherwise, Excel will return a `#NUM!` error.
- If `actual_range` or `expected_range` contains non-numeric values, Excel will return a `#VALUE!` error.

### Additional Considerations:

- The **null hypothesis** tested by `CHITEST` is that there is no significant difference between the observed values and
  the expected values.
- The function directly gives you the p-value; you don't need to manually calculate the chi-squared statistic.

### Use Cases:

- **Goodness-of-Fit Test**: Determine how well the observed data matches an expected distribution.
- **Contingency Table Analysis**: Test for independence between two categorical variables.
- **Hypothesis Testing**: Evaluate whether the differences between data sets are statistically significant.

> **Tip**: Use the `CHISQ.TEST` function in newer versions of Excel as it provides the same functionality but with
improved accuracy.