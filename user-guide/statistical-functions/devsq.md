<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DEVSQ Function

The `DEVSQ` function in Excel calculates the **sum of the squared deviations** of data points from their sample mean. It
is a measure of variability that indicates the total squared differences between each data point and the mean of the
dataset.

This function is commonly used in statistical analysis, particularly for measuring variation or dispersion in data sets,
and can serve as a building block for computations like variance.

### Key Features of DEVSQ:

- Computes the sum of squared deviations for a set of data points.
- Helps identify the overall spread of data points around the mean.
- Often used in conjunction with other statistical measures like variance and standard deviation.
- Non-numeric values and empty cells in the input range are ignored.

### Syntax:

```plaintext
DEVSQ(number1, [number2], …)
```

- **number1**, **number2**, ...: Numerical values or ranges (arrays) to calculate the sum of squared deviations. You can
  input a set of numbers, ranges, or a combination of both.

### Examples:

1. `=DEVSQ(A1:A10)`  
   Calculates the sum of squared deviations for the values in the range `A1:A10`.  
   **Result**: A single numeric value representing the total squared deviations.

2. `=DEVSQ(1, 2, 3, 4, 5)`  
   Computes the sum of squared deviations for the data set `{1, 2, 3, 4, 5}`.  
   **Result**: A numeric value indicating how these numbers deviate from the mean.

3. `=DEVSQ(A1:A5, C1:C5)`  
   Calculates the sum of squared deviations for the combined values in the ranges `A1:A5` and `C1:C5`.  
   **Result**: A numeric value representing the total squared variability in the ranges.

### Notes:

- If a value in the input range is non-numeric (e.g., text), it is ignored in the calculation.
- The result will always be a non-negative number since differences are squared.
- `DEVSQ` is ideal for analyzing the spread of numerical data but does not normalize for the number of elements like
  variance does.
- If analyzing population variance or standard deviation, use `VAR.P` or `STDEV.P` respectively.

> **Tip**: Use the `DEVSQ` function to gain insights into the overall variability of your data set, especially when
analyzing how data points are spread relative to their mean in exploratory data analysis.