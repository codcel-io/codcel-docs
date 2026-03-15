<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VAR Function

The `VAR` function in Excel is used to **estimate the variance based on a sample of data provided**. Variance is a
measure of how much the data points in a dataset deviate from their mean (average value). Use this function when the
data represents only a subset, or sample, of a larger population.

### Key Features of VAR:

- **Sample Variance**: Computes variance for a sample, rather than the entire population.
- **Estimated Analysis**: Assumes the data is a subset and adjusts for this by dividing by `(n-1)` instead of `n`.
- **Statistical Insight**: Useful for understanding the spread or variability in a dataset.

### Syntax:

```plaintext
VAR(number1, [number2], ...)
```

- **number1, number2, ...**: Required. The first number, and subsequent numbers (up to 254), can be entered as arguments
  or as cell ranges.

    - You must provide at least one numeric argument.
    - Data ranges can also be used (e.g., `A1:A10`).

### How It Works:

1. Computes the mean (average) of the given data points.
2. Determines the squared difference between each data point and the mean.
3. Divides the sum of these squared differences by `(n-1)` (where `n` is the total number of data points).

### Examples:

1. **Basic VAR Calculation**:
   To calculate the sample variance for `{3, 5, 7, 9, 11}`:

   ```excel
   =VAR(3, 5, 7, 9, 11)
   ```

    - Step 1: Calculate the mean: `(3 + 5 + 7 + 9 + 11) / 5 = 7`.
    - Step 2: Find squared differences from the mean:
      `[(3-7)^2, (5-7)^2, (7-7)^2, (9-7)^2, (11-7)^2] = [16, 4, 0, 4, 16]`.
    - Step 3: Divide the sum of squared differences by `(n-1)`:
      `(16 + 4 + 0 + 4 + 16) / 4 = 10`.

   Result: `10`.

2. **Using Ranges**:
   For a dataset in cells `B1:B5` containing `3, 5, 7, 9, 11`:

   ```excel
   =VAR(B1:B5)
   ```

   Produces the same result as above.

3. **Larger Dataset**:
   For a dataset stored across cells `C1:C20`:

   ```excel
   =VAR(C1:C20)
   ```

   This estimates the sample variance across all 20 data points provided.

### Notes:

- **Distinction from `VAR.P`**:
    - Use `VAR` when working with a sample.
    - Use `VAR.P` when the dataset contains the entire population, as `VAR.P` does not make the `(n-1)` sample
      adjustment.
- **Non-Numeric Values**:
    - Any text, logical values, or blanks in the range are ignored.
    - Logical values like `TRUE` or `FALSE` are excluded automatically.
- **Error Handling**:
    - If fewer than 2 numeric arguments are provided, Excel returns a `#DIV/0!` error.
    - If invalid data (e.g., non-numeric inputs) is included, Excel may produce a `#VALUE!` error.

### Applications:

- **Statistical Analysis**: Helps in estimating data variability based on a sample in demographics, surveys, and
  science.
- **Data Insights**: Assists in determining how data points in a sample deviate from the mean.
- **Sampling Tasks**: Ideal for datasets where complete population data is unavailable.
- **Predictive Modeling**: Enables a better understanding of data variability for sample-based analysis.

> **Tip**: Use the `VAR.S` function in modern versions of Excel for better clarity, as `VAR` is meant for backward
> compatibility. `VAR` and `VAR.S` perform the same calculation.