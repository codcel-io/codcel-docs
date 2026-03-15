<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PERCENTILE Function

The `PERCENTILE` function in Excel is used to calculate the **k-th percentile of a dataset**, where `k` is a value
between 0 and 1. This function helps identify the value below which a given percentage of data falls.

### Key Features of PERCENTILE:

- **Returns a Specific Percentile**: Allows you to find the value that corresponds to a specific percentage of data in a
  range.
- **Useful for Data Analysis**:
    - Identify thresholds or cutoffs (e.g., the top 10%).
    - Analyze data distribution by dividing it into percentiles.

### Syntax:

```plaintext
PERCENTILE(array, k)
```

- **array**: Required. The set of numeric values for which you want to calculate the percentile.
- **k**: Required. A decimal value between `0` and `1` representing the desired percentile (e.g., `0.5` for the 50th
  percentile, or median).

### How It Works:

`PERCENTILE` calculates the value based on the `k-th` position in the sorted dataset (array). If `k` doesn't correspond
exactly to a position, Excel interpolates between the nearest ranks.

### Examples:

1. **Basic Example**:
   To calculate the 50th percentile (median) of a dataset:
   ```excel
   =PERCENTILE({1, 2, 3, 4, 5}, 0.5)
   ```
   Result: `3` (the middle value of the dataset).

2. **25th Percentile**:
   To find the value below which 25% of your data falls:
   ```excel
   =PERCENTILE({10, 20, 30, 40, 50}, 0.25)
   ```
   Result: `20` (representing the first quartile).

3. **Interpolating Example**:
   If the dataset `{10, 20, 30, 40, 50}` is used to calculate the 65th percentile:
   ```excel
   =PERCENTILE({10, 20, 30, 40, 50}, 0.65)
   ```
   Result: A value between `30` and `40` (interpolated based on `k`).

4. **Extreme Values**:
   To find the minimum value (0th percentile) and maximum value (100th percentile):
   ```excel
   =PERCENTILE({5, 10, 15, 20, 25}, 0)
   ```
   Result: `5` (minimum value of the dataset).

   ```excel
   =PERCENTILE({5, 10, 15, 20, 25}, 1)
   ```
   Result: `25` (maximum value of the dataset).

### Notes:

- **Input Validation**:
    - The `array` must contain numeric values; otherwise, the function returns `#VALUE!`.
    - The `k` value must be between `0` and `1`; otherwise, the function returns the `#NUM!` error.

- **Interpolation**:
    - If `k` does not exactly match any rank, `PERCENTILE` interpolates between the closest values.

- **Alternative Function**:
    - Starting in Excel 2010, the `PERCENTILE` function has been replaced by `PERCENTILE.INC` for better clarity. Excel
      also provides `PERCENTILE.EXC`, which excludes the boundaries (`0` and `1`).

### Applications:

- **Education**: Find the score below which a certain percentage of students fall.
- **Business**: Analyze sales data to identify values in specific percentiles (e.g., bottom 25% or top 10% performers).
- **Statistics**: Calculate quartiles or other percentile-based insights.
- **Finance**: Determine cutoff points for financial performance benchmarks.

> **Tip**: Use `PERCENTILE.INC` for inclusive calculations (including 0% and 100%). Use `PERCENTILE.EXC` if you want to
exclude these boundaries.