<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VAR.S Function

The `VAR.S` function in Excel is used to **calculate the variance of a sample** from a dataset. Variance measures how
dispersed or spread out the numbers in a dataset are relative to the mean.

### Key Features of VAR.S:

- **Sample Variance**: This function is specifically designed for **sample data**, not the entire population. Use
  `VAR.P` if you're working with population data.
- **Measuring Data Spread**: It helps understand the variability or consistency of your data values.
- **Excludes Non-Numerical Data**: Automatically ignores text, logical values, or blank cells in the range.

### Syntax:

```plaintext
VAR.S(number1, [number2], …)
```

- **number1**: Required. The first number, cell reference, or range in your sample dataset.
- **number2, …**: Optional. Additional numbers, cell references, or ranges in your sample dataset.

You can provide numbers directly, or reference ranges or arrays containing numeric values.

### How It Works:

1. Calculates the mean (average) of the provided data.
2. Finds the squared differences of each data point from the mean.
3. Divides the sum of these squared differences by `(n-1)` (where `n` is the sample size) to account for sample-based
   bias.

### Examples:

1. **Basic Use**:

   To calculate the sample variance of `{4, 6, 8, 10, 12}`:

   ```excel
   =VAR.S(4, 6, 8, 10, 12)
   ```

   **Explanation**:
    - Mean = `(4 + 6 + 8 + 10 + 12) / 5 = 8`
    - Squared differences from the mean:
      `(4-8)^2, (6-8)^2, (8-8)^2, (10-8)^2, (12-8)^2 = 16, 4, 0, 4, 16`
    - Sum of squared differences = `16 + 4 + 0 + 4 + 16 = 40`
    - Divide by `(n-1)` = `40 / (5-1) = 40 / 4 = 10`

   Result = `10`

2. **Using a Range**:

   To calculate the sample variance for numbers in the range `A1:A10`:

   ```excel
   =VAR.S(A1:A10)
   ```

   This will compute the variance for all numerical entries in the range `A1:A10`.

3. **Ignoring Non-Numerical Data**:

   If the range `A1:A10` contains both numbers and text (or blank cells), `VAR.S` will exclude non-numeric data and only
   compute the variance for numeric values.

4. **Array Example**:

   You can input an array directly:

   ```excel
   =VAR.S({2, 4, 6, 8, 10})
   ```

   This calculates the sample variance for the numbers in the array `{2, 4, 6, 8, 10}`.

### Notes:

- **Difference Between VAR.S and VAR.P**:
    - `VAR.S` is used for a sample and divides the sum of squared differences by `(n-1)`.
    - `VAR.P` is used for an entire population and divides by `n` instead of `(n-1)`.

- **Error Handling**:
    - If no numeric data is provided, `VAR.S` returns a `#DIV/0!` error.
    - If there is only one numeric value, `VAR.S` also returns a `#DIV/0!` error (since variance requires at least two
      data points).

- **Logical Values**:
    - Logical values and text representations of numbers in arrays/ranges are ignored.

### Applications:

- **Statistical Analysis**: Calculate variability in a small sample of data.
- **Risk Assessment**: Measure the level of risk or fluctuation in financial models.
- **Quality Control**: Analyze stability and consistency in product measurements.

> **Tip**: If you need the standard deviation instead of variance, use the `STDEV.S` function, which is the square root
> of `VAR.S`.