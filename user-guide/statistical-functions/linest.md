<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LINEST Function

The `LINEST` function in Excel is used to calculate the **statistics for a line by fitting a straight line (using the
linear regression method)** to your dataset. It is commonly applied in scenarios involving predictive modeling, trend
analysis, and statistical analysis.

### Key Features of LINEST:

- **Linear Regression Analysis**: Calculates the slope, intercept, and other parameters of a linear equation.
- **Supports Multiple Variables**: Extends functionality to handle multivariable data for advanced regression models.
- **Statistical Outputs**: Optionally returns detailed regression statistics (e.g., standard error, r-squared).

### Syntax:

```plaintext
LINEST(known_y's, [known_x's], [const], [stats])
```

- **known_y's**: The dependent data (y-values) in your linear regression analysis.
- **known_x's**: (Optional) The independent data (x-values). If omitted, Excel assumes `{1, 2, 3, ...}`.
- **const**: (Optional) A logical value:
    - `TRUE` (default): Forces the regression line to include a y-intercept.
    - `FALSE`: Fits the line through the origin (no y-intercept).
- **stats**: (Optional) A logical value:
    - `TRUE`: Returns additional regression statistics in an array.
    - `FALSE` (default): Returns only the slope and intercept.

### How It Works:

The `LINEST` function calculates the equation of a straight line:

```plaintext
y = mx + b
```

- **m**: Slope of the line.
- **b**: Y-intercept.

If used with the `stats` parameter set to `TRUE`, additional statistical values, such as standard errors and regression
coefficients, are returned.

### Examples:

1. **Simple Linear Regression**:

   Given `y-values` as `{1, 2, 3, 4}` and `x-values` as `{5, 6, 7, 8}`, calculate the slope and intercept:

   ```excel
   =LINEST({1, 2, 3, 4}, {5, 6, 7, 8})
   ```
   Result:
    - Slope (`m`) = 1
    - Intercept (`b`) = -4

2. **Force Zero Intercept**:

   Perform linear regression with a forced zero intercept:

   ```excel
   =LINEST(A1:A4, B1:B4, FALSE)
   ```

3. **Include Regression Statistics**:

   Find the slope, intercept, and detailed regression statistics:

   ```excel
   =LINEST(A1:A4, B1:B4, TRUE, TRUE)
   ```
   Result (array output):
    - First row: Slope, intercept.
    - Second row: Standard errors for slope and intercept.
    - Third row: Coefficient of determination (r-squared), standard error of `y-est`.
    - Additional statistical values.

### Notes:

- **Array Formula**: When using `LINEST` with the `stats` parameter set to `TRUE`, you must input it as an array
  formula (hold `Ctrl + Shift + Enter` on older versions of Excel).
- **Data Alignment**: Ensure that `known_y's` and `known_x's` are of the same length. Mismatched ranges will result in a
  `#VALUE!` error.
- Blank cells or text values in the dataset are ignored.

### Applications:

- **Forecasting**: Predict future values based on a linear trend in historical data.
- **Business Analytics**: Analyze relationships between sales and advertising spend, pricing models, etc.
- **Science and Engineering**: Fit experimental data to linear models for further analysis.
- **Financial Modeling**: Analyze market trends, portfolio returns, or pricing patterns.

> **Tip:** Combine `LINEST` with functions like `INDEX`, `TREND`, or `FORECAST` to extract specific regression results
or perform advanced computations.