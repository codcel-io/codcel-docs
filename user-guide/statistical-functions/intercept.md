<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## INTERCEPT Function

The `INTERCEPT` function in Excel is used to calculate the **y-intercept** of the linear regression line for a given set
of data points. This is the point where the regression line crosses the y-axis (i.e., when `x = 0`).

### Key Features of INTERCEPT:

- Computes the y-intercept of the line described by the linear relationship between two datasets (dependent and
  independent variables).
- Useful for statistical forecasting, trend analysis, and finding the starting value of a dataset.
- The calculation assumes a linear relationship between the datasets.

### Syntax:

```plaintext
INTERCEPT(known_ys, known_xs)
```

- **known_ys**: The range or array of dependent values (y-values in the dataset).
- **known_xs**: The range or array of independent values (x-values in the dataset).

### How It Works:

The `INTERCEPT` function calculates the y-intercept using the following equation from the linear regression formula:

```plaintext
y = mx + b
```

Where:

- `m` is the slope of the regression line (calculated from `known_ys` and `known_xs`).
- `b` is the intercept (calculated by the function).
- The y-intercept (b) is returned as the output of the function.

### Examples:

1. **Basic Calculation**:

   Given the following data points:

    - Known Y values: `2, 4, 6`
    - Known X values: `1, 2, 3`

   Use the formula:
    ```excel
    =INTERCEPT({2, 4, 6}, {1, 2, 3})
    ```
   Result: `0`

2. **Using a Range**:

   If `A1:A3` contains y-values (`2, 4, 6`) and `B1:B3` contains x-values (`1, 2, 3`):
    ```excel
    =INTERCEPT(A1:A3, B1:B3)
    ```
   Result: `0`

3. **Forecasting Example**:

   Assume a dataset of sales data (y-values) versus months (x-values). To find the starting sales amount (y-intercept),
   use the sales and time range to calculate the intercept:
    ```excel
    =INTERCEPT(SalesRange, MonthsRange)
    ```
   This will return the baseline sales level.

### Notes:

- **Parameter Constraints**:
    - The `known_ys` and `known_xs` arrays must have the same number of data points, or the function will return an
      error.
    - Blank cells, text, or non-numeric values in the ranges will result in a calculation error.

- The function assumes a linear relationship between the variables; if the data is not linear, the results may not be
  accurate.

- The `INTERCEPT` function can be combined with the `SLOPE` function to fully describe the linear regression equation.

### Applications:

- **Finance**: Predict baseline values for trends like sales, expenses, or revenue.
- **Data Analysis**: Find the starting point for relationships between dependent and independent variables.
- **Statistics**: Define baseline values for regression analysis.

> **Tip:** Use `INTERCEPT` alongside `SLOPE` to evaluate and forecast linear trends in your data.