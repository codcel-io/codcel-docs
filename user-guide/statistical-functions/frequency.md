<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FREQUENCY Function

The `FREQUENCY` function in Excel is used to calculate the **frequency distribution** of a dataset within specified
intervals or bins. It helps analyze how often values occur within certain ranges, making it particularly valuable for
summarizing data and creating histograms.

### Key Features of FREQUENCY:

- Returns a vertical array of frequencies corresponding to specified intervals (bins).
- Useful for quickly summarizing data into ranges (e.g., sales data, scores).
- Often utilized to understand distribution patterns in data, such as how values cluster or spread.

### Syntax:

```plaintext
FREQUENCY(data_array, bins_array)
```

- **data_array**: The array or range of data you want to evaluate the frequency for.
- **bins_array**: The array or range of intervals (bins) that define how you want the data to be grouped.

### How It Works:

The function counts the number of values in `data_array` that fall into each interval specified in `bins_array`.

- The first element in the result corresponds to the count of values less than or equal to the first bin.
- Subsequent elements correspond to values within each bin range.
- The last element corresponds to values greater than the largest bin.

### Examples:

1. **Basic Frequency Distribution:**

   Suppose you have sales data in the range `A1:A10` and want to group them into intervals defined in `B1:B5`:
   ```excel
   =FREQUENCY(A1:A10, B1:B5)
   ```

   This returns an array of frequencies for each interval defined in `B1:B5`.

2. **Creating a Histogram:**

   Combine `FREQUENCY` with a chart to visualize data distribution. Use the function to calculate frequencies and apply
   a column chart to the result to generate a histogram.

3. **Count of Specific Ranges:**

   Let’s say you have scores in `A1:A15` and want to count scores below 50, between 50-75, and above 75. Define bins in
   `B1:B2` as `50` and `75`:
   ```excel
   =FREQUENCY(A1:A15, B1:B2)
   ```

    - The result will include the count of scores below 50, between 50-75, and above 75.

### Notes:

- The `FREQUENCY` function is an **array function**, so it must be entered as an array formula in older versions of
  Excel by pressing `Ctrl+Shift+Enter`. In newer versions (Excel 365 or Excel 2021), it automatically spills into
  adjacent cells if there is space.
- If a value in `data_array` is not numeric, Excel ignores it in the frequency calculation.
- Ensure that the `bins_array` is sorted in ascending order.

### Applications:

- **Statistical Data Analysis:** Understand how values are distributed in data (e.g., scores, sales, etc.).
- **Histogram Preparation:** Quickly calculate frequencies for creating histograms without manual effort.
- **Summarizing Survey Results:** Analyze responses by grouping them into ranges of scores or values.

> **Tip:** Use `FREQUENCY` in conjunction with Excel charts to visually represent data distribution and easily identify
patterns or outliers.