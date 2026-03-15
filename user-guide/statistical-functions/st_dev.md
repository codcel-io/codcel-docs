<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STDEV Function

The `STDEV` function in Excel is used to **estimate the standard deviation** of a set of numerical data. The standard
deviation measures how much the values in a dataset deviate from the mean (average). This function specifically assumes
the data represents a **sample**, not the entire population.

### Key Features of STDEV:

- **Statistical Calculation**: It calculates the amount of variation or dispersion in a dataset.
- **Sample-Based**: It treats the data as a sample, making it ideal for smaller datasets representing a subset of a
  population.
- **Widely Used**: Commonly used in statistics, finance, and data analysis to understand variability.

### Syntax:

```plaintext
STDEV(number1, [number2], ...)
```

- **number1**: Required. The first numeric value or range in the dataset.
- **[number2], ...**: Optional. Additional numbers or ranges to include in the calculation (up to 255 arguments in older
  Excel versions; unlimited in modern Excel).

### How It Works:

The `STDEV` function calculates the standard deviation using the following formula:

```plaintext
s = √[ Σ(xi - x̄)² / (n - 1) ]
```

Where:

- `xi` = Each value in the dataset,
- `x̄` = Mean (average) of the dataset,
- `n` = Total number of data points (sample size).

The denominator `(n - 1)` is used because this formula applies **sample-based standard deviation** (unlike
population-based).

### Examples:

1. **Basic Example**:
   For the dataset `{5, 7, 8, 10, 12}` in cells `A1:A5`, you can calculate the standard deviation as:
   ```excel
   =STDEV(A1:A5)
   ```
   Result: `2.74` (an approximation, depending on Excel settings).

2. **Multiple Ranges**:
   To calculate the standard deviation of data in two separate ranges `A1:A5` and `B1:B5`:
   ```excel
   =STDEV(A1:A5, B1:B5)
   ```

3. **Including Individual Numbers**:
   You can also mix ranges and individual numbers in the arguments. For example:
   ```excel
   =STDEV(A1:A5, 15, 20)
   ```

### Notes:

- **Data Requirements**:
    - The function only works with numeric values.
    - Blank cells, text, and logical values (TRUE/FALSE) are ignored unless directly typed into the formula as
      arguments.

- **Difference from STDEVP**:
    - The `STDEV` function estimates standard deviation for a **sample**.
    - Use `STDEVP` (or `STDEV.P` in modern Excel) when your data represents an **entire population**.

- **Error Handling**:
    - `#DIV/0!`: Occurs if there are fewer than two numeric data points in the dataset.

### Applications:

- **Risk Assessment**: Analyze volatility in financial models.
- **Statistical Analysis**: Measure variability across sample data.
- **Quality Control**: Track deviations from expected standards in datasets related to manufacturing or performance.
- **Data Insights**: Understand how "spread out" a set of data points is from the mean.

> **Tip**: For population data, always use the `STDEVP` (or `STDEV.P`) function to ensure accuracy.