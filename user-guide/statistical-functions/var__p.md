<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VAR.P Function

The `VAR.P` function in Excel is used to **calculate the variance of an entire population based on the data provided**.
Variance is a measure of how much the data points in a dataset deviate from the mean (average value) of the dataset.

### Key Features of VAR.P:

- **Population Variance**: Computes variance for the entire population, not a sample.
- **Precise**: Assumes all data points in the population are available, unlike `VAR.S`, which estimates variance based
  on a sample.
- **Math-Based Analysis**: Helps in understanding data distribution by quantifying the spread of values.

### Syntax:

```plaintext
VAR.P(number1, [number2], ...)
```

- **number1, number2, ...**: Required. The first number, and subsequent numbers (up to 254), which can be entered
  manually as arguments, or as a range of cells containing the data.

    - The function requires at least one numeric argument.
    - You can also input data ranges (e.g., `A1:A10`).

### How It Works:

1. Calculates the mean (average) of all the data points.
2. Determines the squared difference between each data point and the mean.
3. Computes the average of these squared differences, producing the variance.

### Examples:

1. **Basic VAR.P Calculation**:
   To calculate the variance for the entire population `{2, 4, 6, 8, 10}`:

   ```excel
   =VAR.P(2, 4, 6, 8, 10)
   ```

    - Step 1: Calculate the mean: `(2 + 4 + 6 + 8 + 10) / 5 = 6`.
    - Step 2: Find squared differences from the mean:
      `[(2-6)^2, (4-6)^2, (6-6)^2, (8-6)^2, (10-6)^2] = [16, 4, 0, 4, 16]`.
    - Step 3: Average the squared differences: `(16 + 4 + 0 + 4 + 16) / 5 = 8`.

   Result: `8`.

2. **Using Ranges**:
   If the dataset spans a range of cells like `A1:A5` (e.g., `2, 4, 6, 8, 10`):

   ```excel
   =VAR.P(A1:A5)
   ```

   Produces the same result as the example above.

3. **Larger Dataset**:
   For a larger population dataset stored in cells `B1:B20`, you can compute:

   ```excel
   =VAR.P(B1:B20)
   ```

   This calculates the population variance across all 20 data points.

### Notes:

- **Distinction from `VAR.S`**:
    - `VAR.P` is used when your data represents the entire population.
    - `VAR.S` should be used if your data is only a sample of the population.
- **Non-Numeric Values**:
    - Any text, logical values, or blank cells in the range are ignored.
    - Logical values like `TRUE` and `FALSE` are not treated as `1` or `0`.
- **Error Handling**:
    - If no numeric arguments are provided, Excel returns a `#DIV/0!` error.
    - If you pass invalid arguments (non-numeric or inappropriate), Excel will return a `#VALUE!` error.

### Applications:

- **Statistical Analysis**: Used to measure data variability for a complete population in demographics, science, and
  finance.
- **Data Insights**: Helps in determining the degree of spread in data to understand consistency.
- **Predictive Modeling**: Variance is a key concept in machine learning and statistics to measure data distribution.
- **Risk Analysis**: Assists in evaluating uncertainty and variability in financial datasets.

> **Tip**: Use `VAR.P` only when you know the dataset represents the entire population. For sample-based variance
> calculations, switch to the `VAR.S` function for more accurate estimation.
> **Note**: This is exactly the same as VARP.