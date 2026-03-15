<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FTEST Function

The `FTEST` function in Excel is used to calculate the **p-value of an F-test**, which assesses whether there is a
significant difference between the variances of two datasets. This is particularly useful in statistical hypothesis
testing scenarios, such as **ANOVA (Analysis of Variance)** or comparing group variances.

### Key Features of FTEST:

- Returns the probability (p-value) that the variances of two arrays or ranges are significantly different.
- Helps determine whether the assumption of equal variances between groups is reasonable or not.
- Often used in conjunction with other tests, like `TTEST` or regression analysis.

### Syntax:

```plaintext
FTEST(array1, array2)
```

- **array1**: The first dataset or range of values.
- **array2**: The second dataset or range of values.

### Example:

1. **Comparing Variances**  
   Suppose you have the following datasets:  
   **Array1**: `{6, 7, 8, 9, 10}`  
   **Array2**: `{8, 9, 10, 11, 12}`  
   Formula:  
   `=FTEST({6, 7, 8, 9, 10}, {8, 9, 10, 11, 12})`  
   **Result**: The p-value, indicating how likely it is that the variances of the two datasets are equal.

### Notes:

- The **F-test** assumes the data is normally distributed.
- **Output**:
    - If the returned value is **close to 0**, it indicates significant differences in variances.
    - If the returned value is **close to 1**, it indicates no significant difference in variances.
- **Invalid inputs**:
    - If either array contains fewer than two data points, the function will return a `#DIV/0!` error.
    - Non-numeric data or empty cells in the arrays will result in calculation errors.

### Use Cases:

- **Hypothesis Testing**: Use `FTEST` to evaluate the assumption of equality of variances before performing other tests
  such as a t-test or ANOVA.
- **ANOVA Testing**: Aids in verifying equal group variances, which is a primary assumption of ANOVA.
- **Quality Control**: Useful for comparing variability across sample groups in manufacturing or engineering contexts.

> **Tip**: In recent versions of Excel, the `FTEST` function has been replaced by `F.TEST`, which provides the same
functionality but conforms to modern naming conventions.