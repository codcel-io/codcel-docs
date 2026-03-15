<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STEYX Function

The `STEYX` function in Excel is used to **calculate the standard error of the predicted y-value in a linear regression
** for a given set of dependent and independent variables.

### Key Features of STEYX:

- **Measures Accuracy**: Indicates the precision of predicted values derived from the regression line.
- **Based on Linear Regression**: Calculates the standard error specifically for the y-value predictions using the "
  least squares" method.
- **Statistical Analysis**: Useful in evaluating the reliability of predictions made by a linear model.

### Syntax:

```plaintext
STEYX(known_y's, known_x's)
```

- **known_y's**: Required. The dependent data points (y-values).
- **known_x's**: Required. The independent data points (x-values).

### How It Works:

The formula for standard error of the y-value is:

```plaintext
se = √[Σ(ŷᵢ - yᵢ)² / (n - 2)]
```

Where:

- **se** is the standard error of the regression.
- **ŷᵢ** is the predicted y-value for each x-value based on the regression line.
- **yᵢ** is the actual y-value.
- **n** is the total number of data points in the dataset.

The `STEYX` function directly computes this value based on the input data, assuming there is a linear relationship
between the variables.

### Examples:

1. **Simple Linear Regression**:
   Suppose you have two sets of data:
   ```plaintext
   X: {1, 2, 3, 4, 5}
   Y: {2.1, 4.1, 5.9, 8.1, 10.2}
   ```
   To calculate the standard error of the predicted y-value:

   ```excel
   =STEYX({2.1, 4.1, 5.9, 8.1, 10.2}, {1, 2, 3, 4, 5})
   ```

   Result: The function evaluates how much the predicted y-value deviates, on average, from the actual y-value.

2. **Data in Ranges**:
   If `X` values are in cells `A1:A5` and `Y` values are in cells `B1:B5`, the formula is:
   ```excel
   =STEYX(B1:B5, A1:A5)
   ```

### Comparisons with Related Functions:

- **`STEYX` vs `LINEST`**:
    - `STEYX` provides the standard error for the predictions in a linear regression.
    - `LINEST` performs a full regression analysis, returning slope, intercept, and other statistics.
- **`STEYX` vs `RSQ`**:
    - `STEYX` measures prediction accuracy (in terms of standard error).
    - `RSQ` measures the goodness of fit of the regression model (r-squared).

### Notes:

- **Input Requirements**:
    - Both `known_y's` and `known_x's` must contain numeric values.
    - Both arrays should have the same number of data points.
- **Errors**:
    - `#N/A` occurs if the number of `known_y's` and `known_x's` are different.
    - `#DIV/0!` occurs if the number of data points is less than 3 (since at least two degrees of freedom are needed).

### Applications:

- **Regression Analysis**: Assess the accuracy of linear predictions.
- **Forecasting**: Evaluate the uncertainty in predicted trends.
- **Scientific Research**: Analyze the reliability of data fitting to a linear model.
- **Predictive Modeling**: Measure expected variation when using regression equations.

> **Tip**: Use `STEYX` to test the precision of a linear regression model in applications such as forecasting, financial
analysis, and scientific measurements. Pair it with other tools like `LINEST` and `RSQ` for deeper insights into the
regression fit.