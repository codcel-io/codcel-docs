<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOGEST Function

The `LOGEST` function in Excel is used to **calculate an exponential curve that best fits your data**, and returns an
array of values that describe the curve. It is commonly applied in regression analysis to model exponential
relationships between variables.

### Key Features of LOGEST:

- **Exponential Regression**: Fits your data to a curve of the form `y = b * m^x`, where `m` is the base and `b` is the
  constant.
- Can return additional statistics for deeper analysis when entered as an array formula.
- Especially useful for forecasting and analyzing trends in datasets that grow exponentially.

### Syntax:

```plaintext
LOGEST(known_y's, [known_x's], [const], [stats])
```

- **known_y's**: Required. The dependent data values or y-values in the dataset.
- **known_x's**: Optional. The independent data values or x-values in the dataset. If omitted, Excel assumes
  `1, 2, 3, …` as x-values.
- **const**: Optional. A logical value (TRUE/FALSE) indicating whether to force the constant (`b`) to equal 1.
    - `TRUE` (default): Calculate the constant normally.
    - `FALSE`: Force the constant (`b`) to equal 1.
- **stats**: Optional. A logical value indicating whether to return additional regression statistics.
    - `TRUE`: Returns statistics including R-squared, standard errors, etc., as an array.
    - `FALSE` (default): Returns only the exponential coefficients.

### How It Works:

The `LOGEST` function performs an exponential regression analysis by transforming the data to a linear form, applying
the least-squares method to determine the best-fit curve, and then returning the coefficients or statistics that
describe the curve.

### Examples:

1. **Basic Calculation**:

   Suppose you have the following data:
    - Known Y's: `{2, 4, 8, 16}`
    - Known X's: `{1, 2, 3, 4}`

   To calculate the exponential coefficients:
   ```excel
   =LOGEST({2, 4, 8, 16}, {1, 2, 3, 4})
   ```
   Result: The array will return values for `m` (base) and `b` (constant).

2. **Expert Mode with Regression Statistics**:

   Given the same data, to return additional statistics:
   ```excel
   =LOGEST({2, 4, 8, 16}, {1, 2, 3, 4}, TRUE, TRUE)
   ```
   Result: This will return an array with values for `m`, `b`, and supplementary statistical data like R-squared and
   standard errors.

3. **Omitting X-Values**:

   If you omit x-values, Excel assumes them as `{1, 2, 3, 4}`:
   ```excel
   =LOGEST({2, 4, 8, 16})
   ```

### Notes:

- **Array Formula**:
    - When using `LOGEST` with the `stats` parameter set to `TRUE`, you must enter it as an array formula by pressing
      `Ctrl + Shift + Enter` (in older Excel versions).
    - Starting with dynamic array formulas in newer versions, results may automatically spill into adjacent cells.

- **Errors**:
    - If the `known_y's` contain more than one column and `known_x's` is omitted, Excel will return a `#N/A` error.

- **Assumptions**:
    - Data should reflect an exponential growth or decay pattern for better accuracy.
    - Both `known_y's` and `known_x's` must be numeric.

### Applications:

- **Forecasting**: Predict future values in exponentially growing datasets, like population or sales growth.
- **Scientific Analysis**: Model processes that follow exponential relationships.
- **Finance**: Analyze compound interest or growth trends in financial data.
- **Data Analysis**: Fit data to curves for trend identification and extrapolation.

> **Tip:** Pair `LOGEST` with graphing tools to visually validate the regression model or combine it with functions like
`TREND` to extract specific calculated values.