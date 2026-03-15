<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## QUARTILE Function

The `QUARTILE` function in Excel is used to determine a specific quartile of a dataset. Quartiles divide data into four
equal parts, each representing a fourth (25%) of the distribution. This function helps identify the values at the 1st
quartile (25th percentile), median (50th percentile), and 3rd quartile (75th percentile), among others.

### Key Features of QUARTILE:

- Extracts values at specified quartiles in the dataset.
- Useful for analyzing data distributions and statistical analysis.
- The updated equivalent function in modern Excel is `QUARTILE.INC`.

### Syntax:

```plaintext
QUARTILE(array, quart)
```

- **array**: The range or array of values for which you want to calculate the quartile.
- **quart**: Specifies which quartile to return:
    - `0`: Minimum value in the dataset (0th percentile).
    - `1`: 1st quartile (25th percentile).
    - `2`: Median or 2nd quartile (50th percentile).
    - `3`: 3rd quartile (75th percentile).
    - `4`: Maximum value in the dataset (100th percentile).

### Example:

1. **Finding the Median (2nd Quartile)**  
   Suppose you have the dataset `{10, 20, 30, 40, 50}` and want to calculate the median:  
   Formula:  
   `=QUARTILE({10,20,30,40,50}, 2)`  
   **Result**: `30` (the middle value of the dataset).

2. **Calculating the 1st Quartile (25th Percentile)**  
   Using the same dataset but specifying the 1st quartile:  
   Formula:  
   `=QUARTILE({10,20,30,40,50}, 1)`  
   **Result**: `20` (25% of the data lies below this value).

3. **Getting the Maximum Value (4th Quartile)**  
   Formula:  
   `=QUARTILE({10,20,30,40,50}, 4)`  
   **Result**: `50` (the highest value in the dataset).

### Notes:

- **Behavior**:
    - The calculated values are interpolated if needed, based on the dataset.
    - Ensure no blank cells or non-numeric values exist in the dataset.
- **Invalid Inputs**:
    - If the `quart` argument is not between `0` and `4`, Excel returns a `#NUM!` error.
    - If the `array` is empty, Excel also returns a `#NUM!` error.
- **Output**:
    - The returned quartile value depends entirely on the input data distribution. Dataset ordering is automatic and
      does not require manual sorting.

### Use Cases:

- **Data Distribution Analysis**: Identify cut-off points for various sections of data.
- **Statistics & Probability**: Analyze interquartile ranges (IQRs) and outliers in datasets.
- **Business Insights**: Segment data into groups for targeted analysis or reporting.

> **Note**: The `QUARTILE` function is supported for legacy purposes but has been replaced by `QUARTILE.INC` in modern
Excel for consistency with other statistical functions.