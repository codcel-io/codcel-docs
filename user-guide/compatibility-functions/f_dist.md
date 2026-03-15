<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FDIST Function

The `FDIST` function in Excel is used to calculate the probability density or the cumulative probability for the *
*F-distribution**. The F-distribution is commonly used in hypothesis testing, particularly in **ANOVA (Analysis of
Variance)** and **comparing variances** between two datasets.

### Key Features of FDIST:

- Returns the probability or cumulative probability associated with the F-distribution.
- The F-distribution is a statistical distribution used primarily for testing whether two populations have the same
  variance.
- The function allows you to calculate:
    - The **probability density function (PDF)**.
    - The **cumulative distribution function (CDF)** (for values up to the specified one).

### Syntax:

```plaintext
FDIST(x, degrees_freedom1, degrees_freedom2)
```

- **x**: The value of the random variable for the distribution. Must be greater than or equal to 0.
- **degrees_freedom1**: The numerator degrees of freedom. Must be a positive integer.
- **degrees_freedom2**: The denominator degrees of freedom. Must also be a positive integer.

### Example:

1. **Cumulative Probability**  
   `=FDIST(2.5, 5, 10)`  
   Calculates the cumulative probability for a test statistic value of 2.5 with numerator degrees of freedom 5 and
   denominator degrees of freedom 10.  
   **Result**: The cumulative probability up to `x = 2.5`.

### Notes:

- The **F-distribution** is frequently used in hypothesis testing for comparing variances between two groups.
- It is a right-skewed distribution that depends on two parameters: the numerator degrees of freedom (**df1**) and the
  denominator degrees of freedom (**df2**).
- **x < 0** will result in a `#NUM!` error, as the F-distribution is only defined for non-negative values.
- Small degrees of freedom result in a more heavily skewed distribution, while larger degrees of freedom give a
  distribution closer to the standard normal distribution.

### Mathematical Formula Behind FDIST:

The probability density function (PDF) for the F-distribution is:

```plaintext
f(x) = [(df1/df2) * (x^(df1/2 - 1))] / [(B(df1/2, df2/2)) * (1 + (df1 * x) / df2)^(df1+df2)/2]
```

Where:

- **df1** = numerator degrees of freedom.
- **df2** = denominator degrees of freedom.
- **B(a, b)** = Beta function.

For the cumulative distribution function (CDF), the integral of the PDF is computed for values up to `x`.

### Use Cases:

- **ANOVA Testing**: Analyze the variances between groups to determine statistical significance.
- **Variance Comparison**: Test equality of two variances from independent populations.
- **Regression Analysis**: Evaluate multiple models or predictors' significance.

> **Tip**: If you need the inverse of the F-distribution (i.e., find the value of `x` for a given probability), use the
`FINV` function.