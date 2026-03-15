<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## KURT Function

The `KURT` function in Excel is used to calculate the **kurtosis** of a dataset, which measures the sharpness or "
tailedness" of the data distribution. Kurtosis helps to describe the shape of the dataset by analyzing how the tails of
the distribution deviate from a normal distribution.

### Key Features of KURT:

- Computes the kurtosis of a dataset, indicating whether the data is heavily-tailed or light-tailed compared to a normal
  distribution.
- **High kurtosis** indicates heavy tails (outliers are more recurrent), while **low kurtosis** indicates light tails.
- Useful in statistics, data analysis, and risk management for understanding the distribution shape and outlier density.

### Syntax:

```plaintext
KURT(number1, [number2], ...)
```

- **number1, [number2], ...**: The data points in the dataset. You can input up to 255 arguments as individual numbers,
  cell references, or ranges.

### How It Works:

The `KURT` function calculates the kurtosis of a dataset using this formula:

```plaintext
Kurtosis = (n * Σ((xi - x̄)^4) / (Σ((xi - x̄)^2)^2)) - 3
```

Where:

- `n` is the number of data points.
- `xi` is each individual data point.
- `x̄` is the mean of the dataset.
- Kurtosis is adjusted by subtracting 3 to measure excess kurtosis (i.e., how the distribution deviates from a normal
  distribution).

### Examples:

1. **Basic Calculation**:

   Given the dataset `{1, 2, 2, 3, 4, 4, 5}`:
   ```excel
   =KURT(1, 2, 2, 3, 4, 4, 5)
   ```
   Result: `-0.1518`

2. **Using a Range**:

   If `A1:A7` contains the dataset `{1, 2, 2, 3, 4, 4, 5}`:
   ```excel
   =KURT(A1:A7)
   ```
   Result: `-0.1518`

3. **Financial Data Example**:

   Assume you have stock returns data stored in the range `B1:B10`. Use the `KURT` function to assess tail risk in the
   distribution of daily returns:
   ```excel
   =KURT(B1:B10)
   ```

   The result will provide insights into whether the return distribution is more prone to extreme values compared to a
   normal distribution.

### Notes:

- **Parameter Constraints**:
    - You need at least 4 data points for the calculation. Otherwise, the function will return a `#DIV/0!` error.
    - The dataset must contain numeric values; blank cells, text, or non-numeric values will result in an error.

- A kurtosis value of:
    - **0** represents a normal distribution (mesokurtic).
    - **Positive (>0)** indicates a distribution with heavier tails (leptokurtic).
    - **Negative (<0)** indicates a distribution with lighter tails (platykurtic).

### Applications:

- **Finance**: Analyze financial return distributions for tail risk and potential outliers.
- **Quality Control**: Assess product variation and detect potential manufacturing outliers.
- **Data Science**: Understand data distribution shapes and detect anomalies in datasets.
- **Risk Management**: Evaluate distributions with extreme deviations affecting decision-making.

> **Tip:** Combine `KURT` with functions like `MEAN`, `STDEV.P`, and `SKEW` to fully analyze the properties of a
dataset.