<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PERCENTRANK.INC Function

The `PERCENTRANK.INC` function in Excel calculates the **rank of a value as a percentage** of a range of values (
including the boundaries). It is used to find the relative standing of a value within a dataset.

### Key Features of PERCENTRANK.INC:

- **Returns Percentage Rank**: Provides a value between 0 and 1 that indicates the relative position of a specific value
  within a dataset.
- **Includes Boundaries**:
    - If the given value is the lowest in the dataset, the result is `0`.
    - If the given value is the highest in the dataset, the result is `1`.
- Useful for statistical analysis, understanding percentile ranks, and comparison across datasets.

### Syntax:

```plaintext
PERCENTRANK.INC(array, x, [significance])
```

- **array**: Required. The set of data values in which you want to calculate the rank.
- **x**: Required. The specific value whose percentage rank you want to find.
- **significance**: Optional. The number of significant digits to include in the result (default is 3 digits).

### How It Works:

`PERCENTRANK.INC` ranks a value based on its position relative to other values in the provided range. Note that it
handles interpolation if the value does not exactly match one in the dataset.

The function essentially divides the dataset into intervals, and the rank of `x` is calculated as a proportional
position within these intervals. The rank is computed using the formula:

```
rank = (position of x) / (n - 1)
```

where `n` is the number of values in the array.

### Examples:

1. **Basic Example**:
   To calculate the percentage rank of the value `75` in a dataset:
   ```excel
   =PERCENTRANK.INC({50, 60, 70, 80, 90}, 75)
   ```
   Result: `0.5` (indicating that the value `75` is at the mid-point rank of the dataset).

2. **Specifying Significance**:
   To calculate the percentage rank with higher precision (5 significant figures):
   ```excel
   =PERCENTRANK.INC({10, 20, 30, 40, 50}, 35, 5)
   ```
   Result: `0.625` (or `0.62500` with the specified significance).

3. **Interpolation Example**:
   If the value `65` is not present in the dataset `{50, 60, 70, 80, 90}`, Excel will interpolate its rank:
   ```excel
   =PERCENTRANK.INC({50, 60, 70, 80, 90}, 65)
   ```
   Result: `0.375` (as `65` lies between `60` and `70`).

4. **Including Boundaries**:
   If the array is `{10, 20, 30, 40, 50}`, the rank of the smallest (`10`) is `0` and the largest (`50`) is `1`:
   ```excel
   =PERCENTRANK.INC({10, 20, 30, 40, 50}, 10)
   ```
   Result: `0` (the lowest value in the dataset).

   ```excel
   =PERCENTRANK.INC({10, 20, 30, 40, 50}, 50)
   ```
   Result: `1` (the highest value in the dataset).

### Notes:

- **Input Validation**:
    - If `x` is not between the minimum and maximum values of `array`, the function returns `#N/A`.
    - Non-numeric `array` values or significance leads to `#VALUE!`.

- **Boundary Considerations**:
    - The lowest rank is `0`, and the highest rank is `1`.
    - To exclude exact boundaries (`0` and `1`), use the `PERCENTRANK.EXC` function instead.

- **Significance**:
    - If omitted, the result defaults to 3 decimal places.
    - Including additional significant digits can improve precision but does not affect the underlying calculation.

### Applications:

- **Education**: Calculate the percentile rank of a student's score in a class.
- **Business**: Assess performance metrics against predefined benchmarks (e.g., sales figures in a region).
- **Statistics**: Analyze the distribution of data points within a dataset.
- **Finance**: Compare stock or portfolio performances relative to a dataset of peers.

> **Tip**: Use `PERCENTRANK.INC` when you need percentile calculations that include the boundaries (0 and 1). If you
> want a function that excludes the boundaries, consider using `PERCENTRANK.EXC` instead.