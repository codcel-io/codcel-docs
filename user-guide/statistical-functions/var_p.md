<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VARP Function

The `VARP` function in Excel is used to **calculate the variance for an entire population**. Variance measures how far
the data values deviate from the mean (average) of the dataset. This function is particularly useful in statistics when
working with the complete dataset of a population (not a sample).

### Key Features of VARP:

- **Population-Based Calculation**: Assumes that the dataset represents the entire population, not a sample.
- **Measures Dispersion**: Helps assess the variability or spread of the data values around the mean.
- **Squared Deviations**: Calculates variance as the average of squared differences from the mean, making all deviations
  positive.

### Syntax:

```plaintext
VARP(number1, [number2], ...)
```

- **number1, number2, ...**: The numbers, ranges, or references for which you want to calculate the variance. At least
  one input is required.
    - You can provide up to 255 arguments in Excel.

### How It Works:

1. The function calculates the **mean** of the provided numbers.
2. Computes the squared differences between each value and the mean.
3. Averages these squared differences to achieve the variance.

- Formulaically, it calculates:

   ```plaintext
   VARP = (Σ(x - μ)²) / N
   ```
  Where:
    - `x` = each data point
    - `μ` = mean of the dataset
    - `N` = number of data points in the population

### Examples:

1. **Basic Variance Calculation**:
   For the dataset `{4, 6, 8, 10, 12}`:

   ```excel
   =VARP(4, 6, 8, 10, 12)
   ```

   This calculates the variance for the entire population represented by these numbers.

2. **Calculating Variance for Data in a Range**:
   If your population data is stored in cells `A1:A5`:

   ```excel
   =VARP(A1:A5)
   ```

   Excel will calculate the variance for all the values in this range.

3. **Using Mixed Range and Number Inputs**:
   You can mix cell ranges and individual numbers:

   ```excel
   =VARP(A1:A3, 5, 7, 9)
   ```

   This combines the values from `A1:A3` with `5, 7, and 9` for the variance calculation.

### Notes:

- **Dataset Size**:
    - Use `VARP` only when you have data for the entire population.
    - For sample data, use the **`VAR`** function instead, as it adjusts for bias by dividing by `(N-1)` instead of `N`.
- **Handles Numeric Values Only**:
    - Non-numeric values in the input (e.g., text or logical values) are ignored.
    - If the dataset contains errors, Excel will return an error (e.g., `#VALUE!`).

### Applications:

- **Statistical Analysis**: Quantifies the variability in a dataset, which helps in understanding population trends.
- **Quality Control**: Measures consistency and dispersion in production data.
- **Financial Modeling**: Assess the risk or volatility of a set of data points, e.g., stock price fluctuations over
  time.
- **Scientific Experiments**: Analyzes the spread or consistency of results.

> **Tip**: If you're unsure whether your dataset represents the population or just a sample, consider using `VAR` to
> safely account for sample-size bias. Using `VARP` for sample data could underestimate the variance.
> **Note**: This is exactly the same as VAR.P.