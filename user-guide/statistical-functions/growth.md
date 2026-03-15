<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GROWTH Function

The `GROWTH` function in Excel is used to calculate **exponential growth** by predicting future values based on existing
data. This function fits an exponential curve to existing data points and extends this curve to estimate future values.

### Key Features of GROWTH:

- Fits an **exponential trendline** (`y = b * m^x`) to the dataset.
- Outputs predicted `y` values for given `x` values based on the curve.
- Useful for predicting growth patterns like population, sales figures, or other values that exhibit exponential trends.
- Handles both single-column and multi-column data for independent (`x`) variables.
- Known `y` values must be positive; otherwise, the function will return an error.

### Syntax:

```plaintext
GROWTH(known_y's, [known_x's], [new_x's], [const])
```

- **known_y's**: The dependent data values. This is the range of observed `y` values for which the function should
  compute the relationship.
- **known_x's** *(optional)*: The independent data values corresponding to `known_y's`. If omitted, Excel assumes a
  sequential series (1, 2, 3, ...).
- **new_x's** *(optional)*: The data points for which you want to predict corresponding `y` values.
- **const** *(optional)*:
    - `TRUE` or omitted: Allows Excel to calculate the `m^x` curve's `b` value.
    - `FALSE`: Forces `b` to equal 1, fitting the curve purely as `y = m^x`.

### How It Works:

The `GROWTH` function uses the exponential formula:

```plaintext
y = b * m^x
```

- `b` is the base value (intercept).
- `m` is the growth factor (rate of change).
- `x` is the independent variable.
- `y` is the dependent variable being calculated.

If `new_x's` are provided, the function predicts corresponding `y` values. If not, it uses the `known_x's` values.

### Examples:

1. **Basic Prediction**:

   Predict exponential growth for the known `y` values `2`, `4`, and `8`:
   ```excel
   =GROWTH({2, 4, 8})
   ```
   Result: Returns predicted values for the same `x` values.

2. **Using both X and Y**:

   Predict growth for the dataset:
    - `known_y's`: `1.5, 2, 2.7`
    - `known_x's`: `1, 2, 3`
   ```excel
   =GROWTH({1.5, 2, 2.7}, {1, 2, 3})
   ```
   Result: Returns predicted `y` values for the inputs.

3. **Prediction for New Values**:

   Predict future `y` values for `x = 4` and `5`, using:
    - `known_y's`: `1.5, 2, 2.7`
    - `known_x's`: `1, 2, 3`
   ```excel
   =GROWTH({1.5, 2, 2.7}, {1, 2, 3}, {4, 5})
   ```
   Result: Returns predicted `y` values for `x = 4` and `5`.

4. **Forcing `b = 1`**:

   Force the base `b` to be `1` by setting `const` to `FALSE`:
   ```excel
   =GROWTH({2, 4, 8}, , , FALSE)
   ```
   Result: Returns predicted `y` values assuming `y = m^x`.

### Notes:

- **Parameter Constraints**:
    - `known_y's` must contain positive numbers.
    - If `known_x's` are omitted, they default to `1, 2, 3, ...`.
- Non-numeric values (e.g., text or blank cells) will be ignored.
- If the data does not exhibit exponential growth, the results may be misleading.

### Applications:

- **Forecasting**: Sales, population growth, product demand, etc.
- **Financial Analysis**: Compound interest or investment predictions.
- **Scientific Research**: Modeling exponential phenomena like radioactive decay or population studies.

> **Tip:** Use the `GROWTH` function when your data displays exponential growth or when predicting trends based on
exponential relationships.