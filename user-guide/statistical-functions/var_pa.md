<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VARPA Function

The `VARPA` function in Excel is used to **calculate the variance of an entire population considering all values,
including numbers, text, and logical values**. This function ensures all data types are accounted for, making it useful
for analyzing diverse datasets.

### Key Features of VARPA:

- **Population Variance**: Assumes the dataset represents the entire population, not a sample.
- **Handles Non-Numeric Data**: Converts logical values (`TRUE` as `1`, `FALSE` as `0`) and treats text as `0`.
- **Comprehensive Inclusion**: Includes every provided value in its original or converted form.

### Syntax:

```plaintext
VARPA(value1, [value2], ...)
```

- **value1**: Required. The first value, range, or cell reference in the dataset.
- **value2, ...**: Optional. Additional values, ranges, or cell references (up to 254 arguments).

   - Arguments can include numbers, text, logical values, or references.

### How It Works:

1. **Population Variance Formula**:
   The `VARPA` function uses the formula:

   ```plaintext
   Variance = Σ(x - mean)^2 / N
   ```

   Where:
   - `x`: Each data point (converted if necessary).
   - `mean`: The average of all data points.
   - `N`: Total number of data points in the dataset.

2. **Conversion Rules**:
   - Numbers are used as-is.
   - Logical values are converted: `TRUE = 1`, `FALSE = 0`.
   - Text is treated as `0`.
   - Empty cells and errors are ignored.

3. **Inclusion of All Data**:
   Unlike other variance functions such as `VAR.P` or `VARA`, `VARPA` considers all values, including text and logical
   data, in its calculations.

### Examples:

1. **Basic VARPA Calculation**:
   Suppose your dataset consists of numbers, a logical value, and text. To calculate the population variance:

   ```excel
   =VARPA(10, TRUE, "Text", FALSE, 20)
   ```

   - Converted dataset: `{10, 1, 0, 0, 20}`.
   - Mean: `(10 + 1 + 0 + 0 + 20) / 5 = 6.2`.
   - Variance: `[(10-6.2)^2 + (1-6.2)^2 + (0-6.2)^2 + (0-6.2)^2 + (20-6.2)^2] / 5 = 58.56`.

2. **Using Ranges**:
   If your data is stored in a range, such as `A1:A5`, you can use:

   ```excel
   =VARPA(A1:A5)
   ```

   This will include numbers, logical values, and text data from the range in the variance calculation.

3. **Comparison with VAR.P**:
   To exclude text from the calculation, use `VAR.P` instead:

   ```excel
   =VAR.P(10, TRUE, FALSE, 20)
   ```

   Here, only the numbers and logical values are considered (`{10, 1, 0, 20}`), yielding a different result.

### Notes:

- **Key Differences**:
   - **VARPA**: Includes all values—numbers, logical values, and text.
   - **VAR.P**: Focuses only on numeric and logical data (ignoring text).
   - **VARA**: Similar to `VARPA`, but calculates sample variance rather than population variance.

- **Impact of Data Conversion**:
  Including text and logical values can significantly alter the variance if non-numeric data is prevalent.

### Applications:

- **Survey Analysis**: Analyze results where responses include numbers, yes/no choices, or text-based inputs.
- **Inclusive Statistics**: Use for datasets where all values must be considered, regardless of their type.
- **Population Studies**: Useful for calculations where the dataset fully represents the population.

> **Tip**: Use `VARPA` when your dataset includes mixed data types and all values need to be included. For simpler
> numeric analysis, prefer `VAR.P`.