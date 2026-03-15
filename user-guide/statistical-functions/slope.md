<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SLOPE Function

The `SLOPE` function in Excel is used to **calculate the slope of the linear regression line** based on a set of
dependent (`y`) and independent (`x`) data points. The slope represents the rate of change or the steepness of the line,
showing how much `y` changes for each unit change in `x`.

### Key Features of SLOPE:

- **Positive Slope**: If the slope is positive, `y` increases as `x` increases.
- **Negative Slope**: If the slope is negative, `y` decreases as `x` increases.
- **Linear Relationship**: The function assumes a linear relationship between `x` and `y`.

### Syntax:

```plaintext
SLOPE(known_y's, known_x's)
```

- **known_y's**: Required. The range of numeric values representing the dependent variable (`y` values).
- **known_x's**: Required. The range of numeric values representing the independent variable (`x` values).

### How It Works:

The `SLOPE` function calculates the slope of the best-fit line using the following formula:

```math
Slope = Σ[(xi - x̄) * (yi - ȳ)] / Σ[(xi - x̄)²]
```

Where:

- `xi, yi`: Individual `x` and `y` data points.
- `x̄`: Mean of the `x` values.
- `ȳ`: Mean of the `y` values.

This formula determines how much `y` changes as `x` changes on average, based on a linear regression model.

### Examples:

1. **Basic Example**:
   Suppose the `x` values are `{1, 2, 3, 4, 5}` and the `y` values are `{2, 4, 6, 8, 10}`, representing a perfectly
   linear relationship:
   ```excel
   =SLOPE({2, 4, 6, 8, 10}, {1, 2, 3, 4, 5})
   ```
   Result: `2` (The slope indicates that for every 1-unit increase in `x`, `y` increases by 2 units.)

2. **Negative Slope**:
   For `x = {1, 2, 3, 4, 5}` and `y = {10, 8, 6, 4, 2}`:
   ```excel
   =SLOPE({10, 8, 6, 4, 2}, {1, 2, 3, 4, 5})
   ```
   Result: `-2` (This indicates a decrease in `y` by 2 units for every 1-unit increase in `x`.)

3. **Non-linear Data**:
   If `x` and `y` are not perfectly linear, such as `x = {1, 2, 3, 4, 5}` and `y = {3, 5, 7, 11, 13}`:
   ```excel
   =SLOPE({3, 5, 7, 11, 13}, {1, 2, 3, 4, 5})
   ```
   Result: `2.4` (Approximately, showing the average rate of change across the data points.)

### Notes:

- **Data Requirements**:
    - Both arrays must have the same number of data points. Otherwise, Excel will return a `#N/A` error.
    - At least two data points are required in both `x` and `y`.

- **Ignored Values**:
    - Non-numeric data, logical values, and empty cells in the ranges are ignored during calculation.

- **Use Cases**:
    - Predicting outcomes: Calculate the slope of return rates in finance.
    - Understanding trends: Analyze the rate of change in sales, performance metrics, etc.
    - Scientific studies: Model relationships between two variables in experiments.

### Applications:

- **Financial Analysis**: Use SLOPE for trend analysis in stock prices, revenue, or expense data.
- **Statistics and Data Analysis**: Define the regression coefficient in linear models.
- **Forecasting**: Assess relationships between independent and dependent variables for future predictions.

> **Tip**: Pair the `SLOPE` function with `INTERCEPT` to fully define a linear trendline’s equation in the form:

   ```math
   y = mx + b
   ```

Where `m` is the slope (from `SLOPE`) and `b` is the intercept (from `INTERCEPT`).