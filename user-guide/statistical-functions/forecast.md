<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FORECAST Function

The `FORECAST` function in Excel predicts a future value based on existing values by utilizing **linear regression**.
This function is widely used in data analysis and forecasting to estimate outcomes based on historical trends.

### Key Features of FORECAST:

- Performs a **linear regression calculation** to predict future data points.
- Requires a known set of **x-values** and **y-values** (the independent and dependent variables).
- Ideal for predicting outcomes when there is a **linear relationship** between variables.

### Syntax:

```plaintext
FORECAST(x, known_y's, known_x's)
```

- **x**: The value for which you want to predict the corresponding `y`.
- **known_y's**: The dependent data set or the existing `y-values`.
- **known_x's**: The independent data set or the corresponding `x-values`.

### Formula:

The `FORECAST` function is based on the equation of a straight line:

```plaintext
y = a + bx
```

Where:

- `a` is the intercept of the regression line,
- `b` is the slope of the regression line,
- `x` is the input value for which you want to predict `y`.

Excel calculates `a` and `b` using the least-squares method:

- Slope (`b`):
  ```plaintext
  b = Σ((x_i - x̄)(y_i - ȳ)) / Σ((x_i - x̄)^2)
  ```
- Intercept (`a`):
  ```plaintext
  a = ȳ - b * x̄
  ```

Where `x̄` and `ȳ` are the mean values of `known_x's` and `known_y's`, respectively.

### Examples:

1. **Predict future sales:**

   Suppose you have sales data in the range `B1:B5` and the corresponding time periods in `A1:A5`.
   To predict sales for a future period (e.g., `6`), use:

   ```excel
   =FORECAST(6, B1:B5, A1:A5)
   ```

   This calculates the expected value for the 6th time period based on the linear trend.

2. **Forecast based on experimental data:**

   If you have observed values of a dependent variable stored in `C1:C10`, and the independent variable in `D1:D10`, you
   can forecast a value when the independent variable is `15`:

   ```excel
   =FORECAST(15, C1:C10, D1:D10)
   ```

3. **Use with cell references:**

   Suppose the x-value to predict is stored in `E1`, and the known data sets are in `F1:F10` (`y-values`) and `G1:G10` (
   `x-values`). The formula becomes:

   ```excel
   =FORECAST(E1, F1:F10, G1:G10)
   ```

### Notes:

- The `FORECAST` function assumes a linear relationship between `x` and `y`. For non-linear trends, consider other
  forecasting methods.
- The `known_x's` and `known_y's` arrays must have the same length.
- If any values in `known_x's` or `known_y's` are non-numeric, the function returns a `#VALUE!` error.
- If `known_x's` values have zero variance (all values are the same), the function returns a `#DIV/0!` error.

### Applications:

- **Business Forecasting:** Predict future sales, revenue, or inventory levels based on historical data.
- **Scientific Research:** Estimate future data points in experiments with linear trends.
- **Project Management:** Anticipate task completions or project metrics based on previous progress.

> **Tip:** For more advanced statistical forecasting, consider using the `FORECAST.ETS` or `TREND` functions.