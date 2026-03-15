<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PERCENTILE.EXC Function

The `PERCENTILE.EXC` function in Excel is used to **return the k-th percentile of a data set**, where `k` is a
percentile value between 0 and 1 (exclusive). This function is often used in statistical analysis to understand the
distribution of data and locate specific percentiles.

### Key Features of PERCENTILE.EXC:

- **Exclusive Percentiles**: It differs from `PERCENTILE.INC` by calculating percentiles in the range `(0,1)`, excluding
  the 0th and 100th percentiles.
- **Data Distribution Insights**: Useful for identifying thresholds or breakpoints in a dataset, e.g., the top 10% or
  90th percentile.
- **Flexible**: Works with any dataset size as long as there are enough values to calculate the specified percentiles.

### Syntax:

```plaintext
PERCENTILE.EXC(array, k)
```

- **array**: Required. The range of data or array of numeric values.
- **k**: Required. A numerical value between `0` and `1` (exclusive) representing the percentile to be calculated.

### How It Works:

The `PERCENTILE.EXC` function interpolates between values in the dataset to calculate the exact percentile value. For a
dataset with `n` data points, it requires:

1. The sorted dataset.
2. A portion of the data excluding extremes when calculating the requested percentile.

- If `k` results in a fractional rank within the dataset, interpolation is used to estimate the percentile.
- If `k` is too low (≤0) or too high (≥1), the function will return a `#NUM!` error.

### Examples:

1. **Basic Example**:
   To calculate the 90th percentile of a dataset in `A1:A10`:
   ```excel
   =PERCENTILE.EXC(A1:A10, 0.9)
   ```
   Result: Returns the value at the 90th percentile of the data in `A1:A10`.

2. **Non-integer Percentiles**:
   If the dataset is `{5, 7, 8, 12, 20}`, to find the 40th percentile:
   ```excel
   =PERCENTILE.EXC({5, 7, 8, 12, 20}, 0.4)
   ```
   Result: An interpolated value between `7` and `8` (~`7.6`, depending on the data).

3. **Usage with Named Range**:
   Assuming you have named a range `Scores`, and you want the 25th percentile:
   ```excel
   =PERCENTILE.EXC(Scores, 0.25)
   ```
   Result: Returns the value representing the 25th percentile of `Scores`.

### Notes:

- **Range Check**:
    - The `k` value must always be between `0` and `1` exclusive.
    - If `k <= 0` or `k >= 1`, Excel returns a `#NUM!` error.
- **Empty or Insufficient Data**:
    - If `array` is empty or has fewer than two values, a `#NUM!` error is returned.
- **Handling Non-Numeric Data**:
    - Non-numeric values within the range will cause an error.
- **Sorting Not Required**:
    - The function automatically handles sorting internally while processing the data.

### Applications:

- **Business Analysis**: Identify the revenue threshold for the top 1% of customers.
- **Education**: Determine the cutoff scores for percentiles in student performance.
- **Finance**: Locate the top quartile (75th percentile) of stock returns.
- **Research**: Analyze the distribution of experimental results and locate specific thresholds.

> **Tip**: Use `PERCENTILE_INC` if you need inclusive percentiles (0th and 100th percentiles), or `QUARTILE.EXC` for
predefined percentile quartiles.