<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FISHER Function

The `FISHER` function in Excel calculates the **Fisher transformation** of a given number. This mathematical
transformation is often used in statistics, particularly when working with correlation coefficients, to normalize data
or make it more suitable for hypothesis testing and confidence interval estimation.

### Key Features of FISHER:

- Computes the **Fisher transformation** for a given input value.
- Useful when analyzing correlation coefficients, as it stabilizes the variance and converts the correlation to a normal
  distribution for statistical analysis.
- Commonly applied in hypothesis testing and regression analysis involving correlations.

### Syntax:

```plaintext
FISHER(x)
```

- **x**: The value to be transformed. This must be between -1 and 1 (exclusive) since it is often derived from a
  correlation coefficient.

### Formula:

The `FISHER` function implements the following transformation:

```plaintext
FISHER(x) = 0.5 * LN((1 + x) / (1 - x))
```

Where `LN` is the natural logarithm.

### Examples:

1. **Compute the Fisher transformation for a specific value:**

    ```excel
    =FISHER(0.5)
    ```

   This calculates the Fisher transformation for the correlation coefficient `0.5`.

2. **Analyze a series of correlations:**

   Suppose you have multiple correlation coefficients in a dataset and want to normalize them for further statistical
   testing.

   If a correlation coefficient is stored in cell `A1`:

    ```excel
    =FISHER(A1)
    ```

3. **Using Fisher-transformed values in hypothesis testing:**

   Combine the `FISHER` function with other statistical functions to calculate confidence intervals or test hypotheses
   about correlation coefficients.

### Notes:

- If **x** is less than or equal to -1 or greater than or equal to 1, `FISHER` returns the `#NUM!` error, as the
  transformation is not defined for such values.
- This function is often paired with the `FISHERINV` function to revert the Fisher-transformed value back into the
  original scale.

### Applications:

- **Statistical Analysis of Correlations:** Improve the properties of correlation coefficients for significance testing.
- **Hypothesis Testing:** Test hypotheses about population correlations using normalized Fisher-transformed values.
- **Confidence Intervals for Correlation Studies:** Calculate confidence intervals using Fisher-transformed values to
  ensure normality.

> **Tip:** Use `FISHER` in combination with `FISHERINV` to easily switch between the transformed and original scale of
correlation coefficients for statistical analysis.