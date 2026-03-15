<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TTEST Function

The `TTEST` function in Excel is used to **calculate the probability (p-value) associated with a Student's t-test**. It
is typically employed to determine whether there is a significant difference between two data sets, assuming they follow
a normal distribution and may be used for hypothesis testing.

### Key Features of TTEST:

- **Hypothesis Testing**: Commonly used in statistical analysis for comparing two data sets.
- **P-Value Calculation**: Returns the probability of observing the data assuming the null hypothesis is true.
- **Two-Sample Comparisons**: Useful for determining whether the means of two samples are significantly different.

### Syntax:

```plaintext
TTEST(array1, array2, tails, type)
```

- **array1**: Required. The first data set.
- **array2**: Required. The second data set.
- **tails**: Required. Specifies the number of distribution tails:
    - `1`: One-tailed distribution (tests for a difference in one direction).
    - `2`: Two-tailed distribution (tests for a difference in either direction).
- **type**: Required. The type of t-test to perform:
    - `1`: Paired t-test (for two related data sets, such as before-and-after measurements).
    - `2`: Two-sample equal variance (homoscedastic) t-test.
    - `3`: Two-sample unequal variance (heteroscedastic) t-test.

### How It Works:

- The function calculates the p-value based on the data in `array1` and `array2`.
- The p-value indicates the probability of obtaining the observed data under the assumption that the null hypothesis is
  true:
    - A **small p-value** (e.g., < 0.05) suggests the null hypothesis can be rejected.
    - A **large p-value** suggests insufficient evidence to reject the null hypothesis.

### Examples:

1. **One-Tailed Test for Equal Variance**:
   Compare two data sets using a one-tailed t-test, assuming equal variance:
   ```excel
   =TTEST(A1:A10, B1:B10, 1, 2)
   ```

2. **Two-Tailed Paired Test**:
   Test whether there is a significant difference between two related data sets:
   ```excel
   =TTEST(C1:C10, D1:D10, 2, 1)
   ```

3. **Two-Sided Test for Unequal Variance**:
   If the data sets have unequal variance, use the heteroscedastic t-test:
   ```excel
   =TTEST(E1:E15, F1:F15, 2, 3)
   ```

### Notes:

- **Input Validation**:
    - `array1` and `array2` must be numeric.
    - `tails` must be either `1` or `2`.
    - `type` must be `1`, `2`, or `3`.
- **Error Handling**:
    - `#N/A`: If `array1` and `array2` have unequal sizes during a paired t-test (`type = 1`).
    - `#VALUE!`: If non-numeric inputs or invalid arguments are used.
- **Degrees of Freedom**:
    - For `type = 2`, the degrees of freedom are shared by the two arrays.
    - For `type = 3`, the degrees of freedom are calculated independently.

### Applications:

- **Statistical Analysis**: Used to compare population means based on sample data.
- **Hypothesis Testing**:
    - Determine if the difference between sample means is statistically significant.
- **Experimental Design**:
    - Evaluate the efficacy of treatments or interventions in controlled studies.
- **Confidence Intervals**:
    - Assess the range within which the true mean difference likely falls.

> **Tip**: In newer Excel versions, `T.TEST` replaces `TTEST`. It works the same way but uses a different formula
structure for improved accuracy.
> **Note**: The functionality is the same as T.TEST.