<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PEARSON Function

The `PEARSON` function in Excel is used to **calculate the Pearson correlation coefficient** between two sets of data.
The Pearson correlation coefficient measures the strength and direction of a linear relationship between two variables.

### Key Features of PEARSON:

- **Measures Linear Correlation**: It quantifies how closely two datasets are linearly related on a scale from `-1` to
  `1`.
- **Direction of Relationship**:
    - A value close to `1` indicates a strong positive linear correlation.
    - A value close to `-1` indicates a strong negative linear correlation.
    - A value near `0` indicates little to no linear correlation.
- Useful for statistical analysis, data science, forecasting, and understanding relationships between variables.

### Syntax:

```plaintext
PEARSON(array1, array2)
```

- **array1**: Required. Data points of the first dataset (must have at least two numeric values).
- **array2**: Required. Data points of the second dataset (must have at least two numeric values).

### How It Works:

The `PEARSON` function computes the Pearson correlation coefficient using the formula:

```plaintext
r = Σ((xi - mean1) * (yi - mean2)) / (√(Σ(xi - mean1)^2) * √(Σ(yi - mean2)^2))
```

Where:

- `xi` and `yi` are the data points from `array1` and `array2`, respectively.
- `mean1` and `mean2` are the averages of the two datasets.
- `r` is the Pearson correlation coefficient.

### Examples:

1. **Basic Example**:
   To calculate the correlation coefficient between two datasets:
   ```excel
   =PEARSON(A1:A10, B1:B10)
   ```
   Result: Returns the correlation coefficient `r` based on the values in ranges `A1:A10` and `B1:B10`.

2. **Positive Correlation**:
   If a dataset of student study hours (`A1:A5`) and their corresponding test scores (`B1:B5`) shows:
   ```plaintext
   A1:A5 = {2, 4, 6, 8, 10}
   B1:B5 = {50, 60, 70, 80, 90}
   ```
   Using:
   ```excel
   =PEARSON(A1:A5, B1:B5)
   ```
   Result: `1` (perfect positive correlation).

3. **Negative Correlation**:
   If two variables are inversely related (e.g., production time vs. efficiency):
   ```plaintext
   A1:A5 = {10, 8, 6, 4, 2}
   B1:B5 = {50, 60, 70, 80, 90}
   ```
   Using:
   ```excel
   =PEARSON(A1:A5, B1:B5)
   ```
   Result: `-1` (perfect negative correlation).

4. **No Correlation**:
   Consider two unrelated datasets:
   ```plaintext
   A1:A5 = {1, 2, 3, 4, 5}
   B1:B5 = {10, 23, 8, 44, 15}
   ```
   Using:
   ```excel
   =PEARSON(A1:A5, B1:B5)
   ```
   Result: Close to `0` (no significant linear correlation).

### Notes:

- **Input Validation**:
    - Both `array1` and `array2` must have the same number of data points.
    - If any values are non-numeric, the function returns `#VALUE!`.
    - If either array contains fewer than two data points, the function returns `#DIV/0!`.

- **Understanding Results**:
    - **`1`**: Perfect positive linear relationship.
    - **`-1`**: Perfect negative linear relationship.
    - **`0`**: No linear relationship.

- Use `PEARSON` with clean numerical datasets that represent linear relationships. It is not suitable for analyzing
  non-linear relationships or datasets with outlier values that might distort results.

### Applications:

- **Business Analysis**: Evaluate the relationship between sales and advertising spend.
- **Finance**: Assess the correlation between stock prices of two companies.
- **Education**: Determine how study habits affect academic performance.
- **Science**: Analyze correlations between environmental variables, like temperature and ice melt.

> **Tip**: If your data appears non-linear, consider evaluating it with other methods, such as a scatterplot or
non-linear correlation functions.