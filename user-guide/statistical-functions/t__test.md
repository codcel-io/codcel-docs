<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## T.TEST Function

The `T.TEST` function in Excel is used to **calculate the probability associated with a Student's t-test**. This
function is commonly applied in hypothesis testing to determine if two data sets have statistically significant
differences.

### Key Features of T.TEST:

- **Hypothesis Testing**: Helps test the null hypothesis that there is no difference between the means of two data sets.
- **Types of T-Tests**: Supports one-tailed or two-tailed t-tests, as well as paired and independent tests.
- **Statistical Significance**: Provides the p-value, which represents the probability of observing the test result
  under the null hypothesis.

### Syntax:

```plaintext
T.TEST(array1, array2, tails, type)
```

- **array1**: Required. The first data set to compare.
- **array2**: Required. The second data set to compare.
- **tails**: Required. Specifies the number of distribution tails:
    - `1` for a one-tailed test.
    - `2` for a two-tailed test.
- **type**: Required. Specifies the type of t-test to perform:
    - `1` for a paired t-test.
    - `2` for a two-sample equal variance (homoscedastic) t-test.
    - `3` for a two-sample unequal variance (heteroscedastic) t-test.

### How It Works:

The `T.TEST` function compares the means of the two data sets and computes the probability (p-value) that the observed
difference occurred by chance. A smaller p-value indicates stronger evidence against the null hypothesis.

### Examples:

1. **One-Tailed Paired T-Test**:
   Suppose you have two data sets, `A1:A10` and `B1:B10`, and you want to perform a one-tailed paired t-test:

   ```excel
   =T.TEST(A1:A10, B1:B10, 1, 1)
   ```

   This will return the p-value for the paired t-test considering only one tail of the distribution.

2. **Two-Tailed Independent T-Test (Equal Variances)**:
   For two independent data sets with equal variances, `A1:A10` and `B1:B10`, use:

   ```excel
   =T.TEST(A1:A10, B1:B10, 2, 2)
   ```

   This computes the p-value for a two-tailed test assuming equal variance between the two samples.

3. **Two-Tailed T-Test (Unequal Variances)**:
   If the variances of the two independent data sets `A1:A10` and `B1:B10` are not equal, you can use:

   ```excel
   =T.TEST(A1:A10, B1:B10, 2, 3)
   ```

   This calculates the p-value for a two-tailed test assuming unequal variance.

### Notes:

- **Input Validations**:
    - `tails` must be `1` (one-tailed) or `2` (two-tailed). Any other value will result in a `#NUM!` error.
    - `type` must be `1`, `2`, or `3`. Any other value will return a `#NUM!` error.
    - The data sets **must have numeric values**. Non-numeric inputs in `array1` or `array2` will return a `#VALUE!`
      error.

- **p-Value Output**:
    - The function returns the p-value for the specified test. A smaller p-value suggests a statistically significant
      difference between the two data sets.
    - Compare the p-value with your significance level (e.g., 0.05) to determine whether to reject the null hypothesis.

- **Relationship to Other Functions**:
    - Related to `T.INV` and `T.INV.2T`, which can be used to find critical t-values for specific confidence levels.

### Applications:

- **Statistical Testing**: Use `T.TEST` in hypothesis testing to evaluate differences between sample means.
- **Experimental Analysis**: Compare the results of two experimental groups, such as a control group and a test group.
- **Decision-Making**: Assess whether differences in business or scientific data sets are statistically significant.

> **Tip**: Always verify the assumptions of the t-test (normality of data, equality of variances, etc.) before relying
> on the result of `T.TEST`.
> **Note**: The functionality is the same as TTEST.