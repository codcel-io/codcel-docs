<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## QUARTILE.INC Function

The `QUARTILE.INC` function in Excel is used to **return the quartile of a given dataset, including all data points**.
Quartiles divide a dataset into four equal parts and are commonly used in statistics to analyze data distribution and
variability.

This function is particularly helpful for statistical analysis when all data points, including minimum and maximum
values, should be considered.

### Key Features of QUARTILE.INC:

- **Quartile Calculation**: Computes the first quartile (25th percentile), median (50th percentile), and third
  quartile (75th percentile) of a dataset.
- **Inclusivity**: Includes the smallest and largest data points, ensuring all elements of the dataset are factored into
  the quartile calculation.
- **Data Summary**: Provides a comprehensive summary of the dataset by dividing it into four intervals.

### Syntax:

```plaintext
QUARTILE.INC(array, quart)
```

- **array**: Required. The range or array of numerical data values for which to calculate the quartile.
- **quart**: Required. An integer (0, 1, 2, 3, or 4) indicating which quartile to compute:
    - `0`: Returns the minimum value.
    - `1`: Calculates the first quartile (25th percentile).
    - `2`: Returns the median (50th percentile).
    - `3`: Calculates the third quartile (75th percentile).
    - `4`: Returns the maximum value.

### How It Works:

The function divides the dataset into four equal parts, including extreme values (minimum and maximum), and calculates
the required quartile:

- **Minimum (Q0)**: The smallest value in the dataset.
- **First Quartile (Q1)**: The value below which 25% of data falls.
- **Median (Q2)**: The value below which 50% of data falls.
- **Third Quartile (Q3)**: The value below which 75% of data falls.
- **Maximum (Q4)**: The largest value in the dataset.

### Examples:

1. **First Quartile**:
   To calculate the first quartile for the dataset `{3, 7, 8, 5, 12, 14, 21, 13, 18}`:
   ```excel
   =QUARTILE.INC({3, 7, 8, 5, 12, 14, 21, 13, 18}, 1)
   ```
   Result: `7.5`

2. **Median**:
   To find the median (second quartile):
   ```excel
   =QUARTILE.INC({3, 7, 8, 5, 12, 14, 21, 13, 18}, 2)
   ```
   Result: `12`

3. **Third Quartile**:
   To compute the third quartile:
   ```excel
   =QUARTILE.INC({3, 7, 8, 5, 12, 14, 21, 13, 18}, 3)
   ```
   Result: `16.5`

4. **Maximum**:
   To find the maximum value:
   ```excel
   =QUARTILE.INC({3, 7, 8, 5, 12, 14, 21, 13, 18}, 4)
   ```
   Result: `21`

### Notes:

- **Difference Between QUARTILE.INC and QUARTILE.EXC**:
    - `QUARTILE.INC` includes all data points in its calculations.
    - `QUARTILE.EXC` excludes the smallest and largest values from calculations, making it less sensitive to outliers.
- **Valid Data**:
    - The `array` must contain at least 1 data point for the function to work. A dataset with fewer points will result
      in a `#NUM!` error.
- **Error Conditions**:
    - `#NUM!`: If `quart` is less than 0 or greater than 4, or if the dataset is empty.
    - `#VALUE!`: If non-numeric data is passed to the function.

### Applications:

- **Data Analysis**: Summarizing a full dataset with quartile metrics.
- **Performance Measurement**: Determining the spread of data in statistical or financial reports.
- **Statistical Reporting**: Breaking data into interquartile ranges to understand central tendency and variability.
- **Education**: Analyzing scores to organize percentile groups.

> **Tip**: Use `QUARTILE.EXC` for calculations that prioritize excluding extremes and `QUARTILE.INC` for inclusive
results.