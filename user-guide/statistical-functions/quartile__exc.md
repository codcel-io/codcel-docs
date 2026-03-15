<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## QUARTILE.EXC Function

The `QUARTILE.EXC` function in Excel is used to **return the quartile of a given data set, excluding the smallest and
largest values**. Quartiles divide a dataset into four equal parts, providing insights into the spread and distribution
of the data.

This function is particularly useful in statistical analysis for evaluating data variability and detecting outliers.

### Key Features of QUARTILE.EXC:

- **Quartile Calculation**: Computes the first quartile (25th percentile), median (50th percentile), and third
  quartile (75th percentile) of a dataset.
- **Exclusivity**: Uses an exclusive method for calculating quartiles, excluding the smallest and largest data points to
  provide precise results.
- **Data Summary**: Helps summarize a dataset by dividing it into manageable intervals.

### Syntax:

```plaintext
QUARTILE.EXC(array, quart)
```

- **array**: Required. The range or array of numerical data values for which to calculate the quartile.
- **quart**: Required. An integer (1, 2, or 3) indicating which quartile to compute.
    - `1`: Calculates the first quartile (25th percentile).
    - `2`: Calculates the median (50th percentile).
    - `3`: Calculates the third quartile (75th percentile).

### How It Works:

The function divides the dataset into four equal parts, excluding extreme outliers (smallest and largest values), and
calculates:

- **First quartile (Q1)**: The value below which 25% of data falls.
- **Median (Q2)**: The value below which 50% of data falls.
- **Third quartile (Q3)**: The value below which 75% of data falls.

### Examples:

1. **First Quartile**:
   To calculate the first quartile for the dataset `{3, 7, 8, 5, 12, 14, 21, 13, 18}`:
   ```excel
   =QUARTILE.EXC({3, 7, 8, 5, 12, 14, 21, 13, 18}, 1)
   ```
   Result: `7.5`

2. **Median**:
   To find the median (second quartile):
   ```excel
   =QUARTILE.EXC({3, 7, 8, 5, 12, 14, 21, 13, 18}, 2)
   ```
   Result: `12`

3. **Third Quartile**:
   To compute the third quartile:
   ```excel
   =QUARTILE.EXC({3, 7, 8, 5, 12, 14, 21, 13, 18}, 3)
   ```
   Result: `16.5`

### Notes:

- **Difference Between QUARTILE.EXC and QUARTILE.INC**:
    - `QUARTILE.EXC` excludes the smallest and largest values from calculations and is less sensitive to outliers.
    - `QUARTILE.INC` includes all data points in its calculations.
- **Valid Data**:
    - The `array` must contain at least 3 data points. For fewer points, the function returns a `#NUM!` error.
- **Error Conditions**:
    - `#NUM!`: If `quart` is less than 1 or greater than 3, or if fewer than 3 data points are provided.
    - `#VALUE!`: If non-numeric data is passed to the function.

### Applications:

- **Data Analysis**: Summarizing data distribution for better decision-making.
- **Outlier Detection**: Identifying data points outside Q1 or Q3 for further investigation.
- **Statistical Reporting**: Decomposing data into interquartile ranges.
- **Finance**: Determining portfolio performance quartiles.

> **Tip**: Use `QUARTILE.INC` if you want to include all data points in your quartile calculations.