<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FORECAST.LINEAR Function

The `FORECAST.LINEAR` function in Excel is similar to the `FORECAST` function and is used to predict or estimate a
future value along a linear trend. It is a more descriptive name for the same linear regression process seen in earlier
versions of Excel.

### Key Features of FORECAST.LINEAR:

- Predicts a value based on a linear regression model.
- Requires a known set of **x-values** and **y-values** (independent and dependent variables).
- Useful for analyzing data with a **linear relationship**.

### Syntax:

```plaintext
FORECAST.LINEAR(x, known_y's, known_x's)
```

- **x**: The value for which to predict the corresponding `y`.
- **known_y's**: Array of dependent values (`y-values`).
- **known_x's**: Array of independent values (`x-values`).

### Formula:

The function uses this equation for a straight line:

```plaintext
y = a + bx
```

Where:

- `a`: the intercept of the regression line,
- `b`: the slope of the regression line,
- `x`: the value for which `y` is calculated.

Excel calculates `a` (intercept) and `b` (slope) using the least-squares method:

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

1. **Predict sales for a specific time period:**  
   Suppose you have sales data in the range `B1:B5` and the corresponding time periods in `A1:A5`. To predict sales for
   a future period (e.g., `6`), use:
   ```excel
   =FORECAST.LINEAR(6, B1:B5, A1:A5)
   ```

2. **Prediction based on experimental data:**  
   If you have observed values of a dependent variable in `C1:C10` and independent variable in `D1:D10`, you can
   forecast a value when the independent variable is `15`:
   ```excel
   =FORECAST.LINEAR(15, C1:C10, D1:D10)
   ```

3. **Referencing cells for dynamic forecasting:**  
   Assume the x-value to predict is stored in `E1`, and the known datasets are in `F1:F10` as `y-values` and `G1:G10` as
   `x-values`. Use:
   ```excel
   =FORECAST.LINEAR(E1, F1:F10, G1:G10)
   ```

### Notes:

- **Linear Relationship:** The `FORECAST.LINEAR` function assumes a linear relationship between `x` and `y`. For
  non-linear relationships, use other techniques or formulas.
- **Matching Array Lengths:** `known_x's` and `known_y's` arrays must have the same length.
- **Error Cases:**
    - Non-numeric values in `known_x's` or `known_y's` return a `#VALUE!` error.
    - If `known_x's` values have no variance (all the same), it returns a `#DIV/0!` error.

### Applications:

- **Business Forecasting:** Estimate future sales, revenue, or costs based on past trends.
- **Scientific Analysis:** Predict future outcomes from experimental or observational data.
- **Project Management:** Anticipate deadlines or milestones based on historical completion trends.

> **Tip:** For advanced forecasting, consider alternatives like `FORECAST.ETS`, `LINEST`, or `TREND` if the data doesn't
adhere to a linear trend.