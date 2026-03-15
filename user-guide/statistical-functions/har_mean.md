<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## HARMEAN Function

The `HARMEAN` function in Excel is used to calculate the **harmonic mean** of a dataset. The harmonic mean is a type of
average that is particularly useful when dealing with rates, ratios, or datasets where smaller values have greater
significance.

### Key Features of HARMEAN:

- Computes the **harmonic mean**, which is defined as the reciprocal of the arithmetic mean of reciprocals.
- Especially valuable for datasets involving rates (e.g., speed, efficiency, etc.).
- Returns an accurate average for unevenly distributed data when high or low values disproportionately affect the
  result.
- All input values must be positive — negative or zero values will result in an error.

### Syntax:

```plaintext
HARMEAN(number1, [number2], ...)
```

- **number1**: The first number or range of values for which to calculate the harmonic mean (required).
- **number2, ...** *(optional)*: Additional numbers or ranges to include in the harmonic mean calculation.

### How It Works:

The formula for the harmonic mean is:

```plaintext
HARMEAN = n / (SUM(1 / x_i))
```

Where:

- `n` is the total number of values.
- `x_i` represents each individual value in the dataset.

### Examples:

1. **Basic Calculation**:

   Calculate the harmonic mean of `4` and `8`:
   ```excel
   =HARMEAN(4, 8)
   ```
   Result: `5.3333`.

2. **Multiple Values**:

   Calculate the harmonic mean of `1`, `2`, `3`, `4`, and `5`:
   ```excel
   =HARMEAN(1, 2, 3, 4, 5)
   ```
   Result: `2.1898`.

3. **Using a Range**:

   Calculate the harmonic mean for values in the range `A1:A5`:
   ```excel
   =HARMEAN(A1:A5)
   ```

4. **Handling Positive Data Points**:

   If you attempt to include zero or negative values, such as:
   ```excel
   =HARMEAN(1, 2, -3)
   ```
   Result: Excel will return an error (#NUM!) because the values must all be positive.

### Notes:

- **Parameter Constraints**:
    - Ensure all dataset values are positive. Zero or negative values cause errors.
- Empty cells, non-numeric values, or text in the given range will be ignored.
- The harmonic mean will always be less than or equal to the arithmetic mean for positive datasets.
- Useful when aggregating rates or ratios, such as in speed or financial rate calculations.

### Applications:

- **Financial Analysis**: Calculating average rates of return for investments or financial instruments.
- **Travel/Speed Problems**: Determining the average speed when traveling different distances at varying speeds.
- **Science and Engineering**: Averaging ratios in harmonic processes or energy transfer rates.

> **Tip:** Use the `HARMEAN` function for datasets involving rates or ratios, as it provides a more accurate average
compared to other mean types in these cases.