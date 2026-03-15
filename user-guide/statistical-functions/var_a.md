<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VARA Function

The `VARA` function in Excel is used to **calculate the variance of a sample**, but it evaluates both numeric and
non-numeric data. Unlike `VAR.S`, this function includes logical values and text in its calculations, assigning specific
numeric values to them (e.g., `TRUE` as `1` and `FALSE` or text as `0`).

### Key Features of VARA:

- **Measures Variation**: Indicates how spread out the sample data is around its mean.
- **Handles Mixed Data Types**: Evaluates logical values and text alongside numbers.
- **Sample-Based Calculation**: Applies Bessel's correction (divides by `n-1`), used for sample datasets.

### Syntax:

```plaintext
VARA(value1, [value2], …)
```

- **value1**: Required. The first value, cell reference, or range to evaluate.
- **value2, …**: Optional. Additional values, cell references, or ranges (up to 254 arguments).

### How It Works:

The formula for sample variance is:

```plaintext
s² = Σ(xᵢ - x̄)² / (n - 1)
```

Where:

- **xᵢ** is each individual data point (including treated logical and text values).
- **x̄** is the sample mean.
- **n** is the total number of data points in the sample.

### Data Evaluation Rules:

For non-numeric data in the input:

- **Logical Values**:
    - `TRUE` is treated as `1`.
    - `FALSE` is treated as `0`.
- **Text**:
    - Any text (even numbers entered as text) is treated as `0`.

### Examples:

1. **Simple Calculation with Mixed Types**:
   Consider the dataset `{10, TRUE, FALSE, "text", 30}`. To calculate the sample variance:
   ```excel
   =VARA(10, TRUE, FALSE, "text", 30)
   ```
    - Logical values are treated as `1` (TRUE) and `0` (FALSE).
    - Text is treated as `0`.
    - Converted dataset: `{10, 1, 0, 0, 30}`.
    - Mean: `(10 + 1 + 0 + 0 + 30) / 5 = 8.2`.
    - Result: `167.2`.

2. **Using Cell Ranges**:
   If the dataset is in cells `A1:A5` with values `{10, TRUE, FALSE, "text", 30}`, the formula:
   ```excel
   =VARA(A1:A5)
   ```
   Yields the same result as above.

3. **Combination of Ranges and Values**:
   For a dataset spread across `A1:A3` and `{20, FALSE}` as additional values:
   ```excel
   =VARA(A1:A3, 20, FALSE)
   ```

### Comparisons with Related Functions:

- **`VARA` vs `VAR.S`**:
    - `VARA` includes logical values and text in calculations.
    - `VAR.S` ignores logical values and text.

- **`VARA` vs `VAR.P` and `VARPA`**:
    - Use `VAR.P` or `VARPA` for entire population calculations.
    - `VARPA` includes logical values and text, similar to `VARA`.

- **`VARA` vs `STDEVA`**:
    - Both include all data types and use sample-based calculations.
    - `VARA` returns the variance; `STDEVA` returns the standard deviation (the square root of the variance).

### Notes:

- **Data Type Inclusion**:
    - Use `VARA` when logical values and text are intentionally part of the dataset.
    - Inputs that are empty cells are ignored.
- **Errors**:
    - `#DIV/0!` occurs if there are fewer than two data points after evaluation (e.g., all empty cells).
- **Performance Tip**:
    - When dealing exclusively with numbers, prefer `VAR.S` for faster computation.

### Applications:

- **Mixed Datasets**: Analyze variation in datasets with a mix of numeric and logical/text values.
- **Survey Data**: Calculate variability in datasets where responses include `TRUE`/`FALSE` or text.
- **Experimental Analysis**: Assess datasets containing both qualitative and numeric measurements.

> **Tip**: Use `VARA` when logical values and text need to be factored into the variance calculation. For strict numeric
> analysis, switch to `VAR.S` or `VAR.P`.