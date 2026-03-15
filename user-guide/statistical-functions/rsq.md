<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RSQ Function

The `RSQ` function in Excel is used to **return the square of the Pearson product moment correlation coefficient (r)**
between two sets of data points. It measures how well the trendline represents the data, indicating the proportion of
the variance in the dependent variable that is predictable from the independent variable.

### Key Features of RSQ:

- **Correlation Strength**: Provides the square of the correlation coefficient (`r^2`), a value between `0` and `1`,
  representing the strength of the relationship.
- **Linear Relationships**: Specifically useful for analyzing linear relationships between two sets of data.
- **Data Comparison**: Requires two datasets with equal lengths for comparison.

### Syntax:

```plaintext
RSQ(known_y's, known_x's)
```

- **known_y's**: Required. The range or array of dependent data points.
- **known_x's**: Required. The range or array of independent data points.

### How It Works:

The `RSQ` function calculates the **r-squared** value by squaring the Pearson correlation coefficient between the two
datasets. The result explains the proportion of variation in the dependent variable (**known_y's**) that can be
explained by the independent variable (**known_x's**) in a linear regression context:

- A result of `1`: Represents a perfect linear relationship (all data points fit the trendline exactly).
- A result closer to `0`: Indicates a weaker relationship or less fit to a linear model.

### Examples:

1. **Simple Linear Correlation**:
   To calculate `RSQ` for dependent values `{2, 4, 6, 8}` and independent values `{1, 2, 3, 4}`:
   ```excel
   =RSQ({2, 4, 6, 8}, {1, 2, 3, 4})
   ```
   Result: `1` (Perfect linear relationship, as the values align exactly).

2. **Partial Fit**:
   For data points `{3, 7, 5, 10}` (dependent) and `{1, 2, 3, 4}` (independent):
   ```excel
   =RSQ({3, 7, 5, 10}, {1, 2, 3, 4})
   ```
   Result: `0.757` (Indicates a reasonably strong fit to a linear model).

3. **No Fit**:
   For data points `{1, 1, 1, 1}` (dependent) and `{1, 2, 3, 4}` (independent):
   ```excel
   =RSQ({1, 1, 1, 1}, {1, 2, 3, 4})
   ```
   Result: `0` (No relationship, as the dependent variable does not change).

### Notes:

- **Data Length**:
    - Both `known_y's` and `known_x's` must have the same number of values. If not, an `#N/A` error is returned.
- **Non-Numeric Data**:
    - Non-numeric values in the datasets are ignored in calculations.
- **Empty Inputs**:
    - If either dataset is empty or contains only a single data point, the function returns a `#DIV/0!` error.
- **Proportion Measure**:
    - The `RSQ` value explains how much variance in `known_y's` is accounted for by `known_x's` but does not indicate
      the direction of the relationship.

### Applications:

- **Statistics and Data Science**: Identify how well a linear model fits real-world data.
- **Research and Analysis**: Measure the explanatory power of an independent variable on a dependent variable.
- **Forecasting**: Evaluate the reliability of predicted models based on historical data.
- **Machine Learning**: Help assess predictive power in linear regression models.

> **Tip**: If you need the actual correlation coefficient (`r`), use the `CORREL` function instead.