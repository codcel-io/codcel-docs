<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## GEOMEAN Function

The `GEOMEAN` function in Excel is used to compute the **geometric mean** of a given set of positive numerical values.
The geometric mean is a type of average that is especially effective for datasets with values in a multiplicative
relationship or varying orders of magnitude, such as growth rates, returns, or probabilities.

### Key Features of GEOMEAN:

- Computes the central tendency of a dataset by multiplying all the values together and taking the nth root (where `n`
  is the total number of values).
- Suitable for analyzing proportional or percentage-based datasets, such as interest rates or investment returns.
- Ensures that the influence of extreme values is balanced compared to the arithmetic mean, making it ideal for skewed
  data.
- All input values **must be positive**; the function will return an error if any value is zero or negative.

### Syntax:

```plaintext
GEOMEAN(number1, [number2], …)
```

- **number1, number2, …**: The set of positive numeric values for which the geometric mean will be calculated. These can
  be individual numbers, cell references, or ranges.

### How It Works:

The `GEOMEAN` function computes the geometric mean using the formula:

```plaintext
GEOMEAN = (Value1 × Value2 × … × ValueN) ^ (1 / N)
```

Here:

- `Value1, Value2, …, ValueN` are the numeric inputs.
- `N` is the total number of values.

This represents the nth root of the product of all numbers, giving a value consistent with proportional growth.

### Examples:

1. **Basic Calculation**:

   Calculate the geometric mean of the numbers `4`, `5`, and `8`:
   ```excel
   =GEOMEAN(4, 5, 8)
   ```
   Result: `5.192`

2. **Using a Range**:

   Calculate the geometric mean of values stored in cells `A1:A5`:
   ```excel
   =GEOMEAN(A1:A5)
   ```
   Result depends on the data in the specified range.

3. **Growth Rate Example**:

   Compute the average annual return for an investment with yearly returns of `10%`, `15%`, and `12%`:
   ```excel
   =GEOMEAN(1.10, 1.15, 1.12) - 1
   ```
   Result: `0.1234` or `12.34%`.

### Notes:

- **Parameter Constraints**:
    - All input values must be greater than zero.
    - Blank cells, text, or negative/zero values will result in an error.

- The `GEOMEAN` function is highly sensitive to zeros and negative values because they invalidate the product in the
  calculation.

### Applications:

- **Finance**: Compute average growth rates for investments or portfolios.
- **Statistics**: Analyze central tendencies for multiplicative datasets.
- **Data Analysis**: Evaluate datasets where extreme values can distort the arithmetic mean.

> **Tip:** Use `GEOMEAN` when the dataset involves rates of change, ratios, or when the data has a multiplicative
relationship between values.