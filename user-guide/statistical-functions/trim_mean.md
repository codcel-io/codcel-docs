<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TRIMMEAN Function

The `TRIMMEAN` function in Excel is used to **calculate the mean (average) of a data set excluding a specified
percentage of data points from the top and bottom**. This is useful for reducing the impact of outliers on the average
and generating a more robust central value.

### Key Features of TRIMMEAN:

- **Excludes Outliers**: Removes a fraction of data points from the extremes (both top and bottom) based on the
  percentage you specify.
- **Robust Average**: Helps avoid distortion of the mean caused by extreme values.
- **Flexible Input**: Allows you to adjust the trimming percentage according to your needs.

### Syntax:

```plaintext
TRIMMEAN(array, percent)
```

- **array**: Required. The range or array of numbers you want to calculate the trimmed mean for.
- **percent**: Required. The fraction of data to exclude, represented as a decimal (for example, `0.2` for 20%).

    - The total fraction is evenly split between the highest and lowest values in the dataset.
    - E.g., a `0.2` percentage would exclude 10% from the bottom and 10% from the top.

### How It Works:

1. The function sorts the data in the `array`.
2. Removes the specified percentage of data points evenly from both the top and bottom of the range.
3. Calculates the mean of the remaining data.

### Examples:

1. **Basic TRIMMEAN Calculation**:
   Exclude 20% of the data from both ends and calculate the mean for the dataset `{4, 6, 8, 12, 14, 16, 18}`:

   ```excel
   =TRIMMEAN({4, 6, 8, 12, 14, 16, 18}, 0.2)
   ```

   This removes 20% of the data (1 value from the top and 1 from the bottom) and calculates the mean of
   `{6, 8, 12, 14, 16}`.

2. **Handling Large Data Ranges**:
   If you have a dataset spread across a worksheet (e.g., in cells `A1:A100`) and want to exclude the top and bottom
   10%, you can use:

   ```excel
   =TRIMMEAN(A1:A100, 0.1)
   ```

   This excludes 10% of the total number of data points (5% from each end).

3. **Rounded Exclusions**:
   If the number of excluded points isn't a whole number, Excel will round to the nearest integer. For example, with a
   25% trimming percentage applied to a dataset of 10 numbers:

   ```excel
   =TRIMMEAN({10, 20, 30, 40, 50, 60, 70, 80, 90, 100}, 0.25)
   ```

   25% equals 2.5 data points to exclude. Excel rounds this to `2` points removed from the top and bottom, leaving
   `{30, 40, 50, 60, 70, 80}` for calculating the mean.

### Notes:

- **Input Validations**:
    - The `percent` value must be between `0` and `1` (inclusive). Otherwise, Excel will return a `#NUM!` error.
    - The `array` must contain numeric values. If the array contains non-numeric values, Excel will return a `#VALUE!`
      error.
- **Rounding Rules**:
    - The number of excluded data points is rounded to the nearest integer.

  For example:
    - In an array of 15 data points, a `10%` trimming percentage (`0.1`) would exclude approximately 2 total points (1
      from the top and 1 from the bottom).

### Applications:

- **Data Cleaning**: Useful for calculating averages when working with datasets that include extreme outliers.
- **Statistical Analysis**: Helps measure central tendency in a more robust way by reducing the influence of outliers.
- **Financial Forecasting**: Excludes abnormal spikes or drops in data when calculating projected averages.
- **Scientific Research**: Commonly used in experiments to minimize the impact of anomalies on the overall mean.

> **Tip**: Use the `TRIMMEAN` function whenever you need a reliable average for data with potential outliers. For
> datasets without outliers, the usual `AVERAGE` function may suffice.