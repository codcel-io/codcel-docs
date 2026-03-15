<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PERCENTILE.INC Function

The `PERCENTILE.INC` function in Excel is used to **return the k-th percentile of a data set**, where `k` is a
percentile value between 0 and 1 (inclusive). This function is commonly used in statistical analysis to understand the
distribution of data or to find specific thresholds.

### Key Features of PERCENTILE.INC:

- **Inclusive Percentiles**: Allows calculations that include the 0th and 100th percentiles, unlike `PERCENTILE.EXC`
  which excludes them.
- **Data Analysis Tool**: Useful for identifying key metrics such as top percentages (e.g., the 90th percentile) or
  median values (50th percentile).
- **Works with All Dataset Sizes**: Can handle various dataset sizes provided there is enough data to calculate the
  specified percentile.

### Syntax:

```plaintext
PERCENTILE.INC(array, k)
```

- **array**: Required. The range of data or array of numeric values.
- **k**: Required. A numerical value between `0` and `1` (inclusive), indicating the desired percentile.

### How It Works:

The `PERCENTILE.INC` function interpolates between values in the dataset to calculate the percentile value. For a
dataset
with `n` data points:

1. The dataset must be sorted (Excel handles this automatically during computation).
2. If `k` specifies a fractional rank, the function uses interpolation to estimate the percentile value.
3. If `k` corresponds to an exact rank in the dataset, the corresponding element is returned.

- If `k` is outside the range `[0, 1]`, Excel will return a `#NUM!` error.

### Examples:

1. **Basic Example**:
   To calculate the 90th percentile of a dataset in `A1:A10`:
   ```excel
   =PERCENTILE.INC(A1:A10, 0.9)
   ```
   Result: Returns the value at the 90th percentile of the data in `A1:A10`.

2. **Median Value**:
   To calculate the 50th percentile (median) for `{3, 5, 7, 9, 11}`:
   ```excel
   =PERCENTILE.INC({3, 5, 7, 9, 11}, 0.5)
   ```
   Result: `7`, which is the exact middle value.

3. **Interpolated Result**:
   If the dataset is `{10, 20, 30, 40, 50}`, to find the 33rd percentile:
   ```excel
   =PERCENTILE.INC({10, 20, 30, 40, 50}, 0.33)
   ```
   Result: An interpolated value (~23.2, depending on the data).

4. **Usage with Named Range**:
   Assuming you have named the range `Scores` and want to find the 25th percentile:
   ```excel
   =PERCENTILE.INC(Scores, 0.25)
   ```
   Result: Returns the value corresponding to the 25th percentile of `Scores`.

### Notes:

- **Range Check**:
    - The `k` value must always be between `0` and `1` inclusive.
    - If `k < 0` or `k > 1`, Excel will return a `#NUM!` error.
- **Empty Datasets**:
    - If `array` is empty or has insufficient data, a `#NUM!` error will be produced.
- **Handling Non-Numeric Data**:
    - Non-numeric values in the range will cause errors during calculation.
- **Automatic Sorting**:
    - The function automatically sorts the dataset internally without requiring manual intervention.

### Applications:

- **Business**: Identify customer purchase thresholds to classify into percentiles.
- **Education**: Find percentile-based grading cutoffs (e.g., 90th percentile top performers).
- **Finance**: Analyze investment returns for specific percentile ranges.
- **Research**: Pinpoint specific thresholds in experimental data distributions.

> **Tip**: Use `PERCENTILE.EXC` if you need exclusive percentiles (excluding 0th and 100th percentiles),
> or `QUARTILE.INC` for predefined percentile quartiles.