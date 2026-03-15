<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TREND Function

The `TREND` function in Excel is used to **return values along a linear trend** that fits your data points. It is
commonly used in forecasting and regression analysis to determine and extend patterns in data.

### Key Features of TREND:

- **Linear Regression Analysis**: Calculates the best-fit line for your data using the method of least squares.
- **Data Forecasting**: Predicts y-values for given x-values based on the identified linear trend.
- **Flexible Data Input**: Works with both complete and partial data sets, and can extrapolate beyond the given range.

### Syntax:

```plaintext
TREND(known_y's, [known_x's], [new_x's], [const])
```

- **known_y's**: Required. The known dependent y-values (e.g., observed results or outputs).
- **known_x's**: Optional. The known independent x-values (e.g., input values). If omitted, Excel assumes
  `{1, 2, 3, ...}`.
- **new_x's**: Optional. The x-values for which you want to predict corresponding y-values. If omitted, Excel returns
  y-values for the given x-values.
- **const**: Optional. A logical value:
    - `TRUE` or omitted if you want Excel to calculate the y-intercept.
    - `FALSE` to force the y-intercept to be `0`.

### How It Works:

The `TREND` function uses the formula for a straight line:

```plaintext
y = mx + b
```

Where:

- `m` is the slope of the line.
- `b` is the y-intercept.
- It determines `m` and `b` using the least squares method based on the provided `known_x's` and `known_y's`.

### Examples:

1. **Basic Trend Prediction**:
   Given the y-values `{2, 4, 6}` and corresponding x-values `{1, 2, 3}`, predict the y-value for `x = 4`:

   ```excel
   =TREND({2, 4, 6}, {1, 2, 3}, {4})
   ```

   This will return the next value in the trend, which is `8`.

2. **Extrapolating Values**:
   If you only know the y-values `{5, 10, 15}` and omit the x-values, you can use:

   ```excel
   =TREND({5, 10, 15},,, TRUE)
   ```

   This calculates the trend assuming `x` is `{1, 2, 3}`, and you can extend it further.

3. **Forcing Zero Intercept**:
   To calculate values along a trend where the line must pass through the origin (`b = 0`), use the `const` argument:

   ```excel
   =TREND({3, 6, 9}, {1, 2, 3}, {4, 5}, FALSE)
   ```

   Here, the values are calculated with the intercept set to `0`.

4. **Using Arrays**:
   If you have multiple `new_x's` and want to return an array, use:

   ```excel
   =TREND({2, 4, 6}, {1, 2, 3}, {4, 5, 6})
   ```

   This will return an array of predicted y-values `{8, 10, 12}`.

### Notes:

- **Input Validations**:
    - The number of `known_y's` must match the number of `known_x's` unless `known_x's` is omitted.
    - Non-numeric or invalid inputs will result in an error.
- **Errors**:
    - `#N/A` error if `new_x's` contains values outside the range of `known_x's` with insufficient data for calculation.
    - `#VALUE!` if non-numeric values are included in the arguments.

### Applications:

- **Forecasting & Budgeting**: Predict future sales, expenses, or other trends.
- **Data Analysis**: Identify linear relationships within datasets.
- **Scientific Studies**: Fit experimental data to a linear model.
- **Business Trends**: Analyze historical data to create projections for growth or decline.

> **Tip**: The `TREND` function is incredibly useful for creating predictive models in Excel. For more sophisticated
> regression analysis, consider using the `LINEST` function.