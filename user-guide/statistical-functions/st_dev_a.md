<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STDEVA Function

The `STDEVA` function in Excel is used to **calculate the standard deviation of a sample**, but it evaluates both
numeric and non-numeric data. Unlike `STDEV.S`, this function includes logical values and text in its calculations,
assigning specific numeric values to them (e.g., `TRUE` as `1` and `FALSE` or text as `0`).

### Key Features of STDEVA:

- **Measures Variation**: Indicates how spread out the sample data is around its mean.
- **Handles Mixed Data Types**: Evaluates logical values and text alongside numbers.
- **Sample-Based Calculation**: Applies Bessel's correction (divides by `n-1`), used for sample datasets.

### Syntax:

```plaintext
STDEVA(value1, [value2], …)
```

- **value1**: Required. The first value, cell reference, or range to evaluate.
- **value2, …**: Optional. Additional values, cell references, or ranges (up to 254 arguments).

### How It Works:

The formula for sample standard deviation is the same as for `STDEV.S`:

```plaintext
s = √[Σ(xᵢ - x̄)² / (n - 1)]
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
   Consider the dataset `{10, TRUE, FALSE, "text", 30}`. To calculate the sample standard deviation:
   ```excel
   =STDEVA(10, TRUE, FALSE, "text", 30)
   ```
    - Logical values are treated as `1` (TRUE) and `0` (FALSE).
    - Text is treated as `0`.
    - Result: `12.91`.

2. **Using Cell Ranges**:
   If the dataset is in cells `A1:A5` with values `{10, TRUE, FALSE, "text", 30}`, the formula:
   ```excel
   =STDEVA(A1:A5)
   ```
   Yields the same result as above.

3. **Combination of Ranges and Values**:
   For a dataset spread across `A1:A3` and `{20, FALSE}` as additional values:
   ```excel
   =STDEVA(A1:A3, 20, FALSE)
   ```

### Comparisons with Related Functions:

- **`STDEVA` vs `STDEV.S`**:
    - `STDEVA` includes logical values and text in calculations.
    - `STDEV.S` ignores logical values and text.

- **`STDEVA` vs `STDEV.P` and `STDEVPA`**:
    - Use `STDEV.P` or `STDEVPA` for entire population calculations.
    - `STDEVPA` includes logical values and text, similar to `STDEVA`.

### Notes:

- **Data Type Inclusion**:
    - Use `STDEVA` when logical values and text are intentionally part of the dataset.
    - Inputs that are empty cells are ignored.
- **Errors**:
    - `#DIV/0!` occurs if there are fewer than two data points after evaluation (e.g., all empty cells).
- **Performance Tip**:
    - When dealing exclusively with numbers, prefer `STDEV.S` or `STDEV.P` for faster computation.

### Applications:

- **Mixed Datasets**: Analyze variation in datasets with a mix of numeric and logical/text values.
- **Survey Data**: Calculate variability in datasets where responses include `TRUE`/`FALSE` or text.
- **Experimental Analysis**: Assess datasets containing both qualitative and numeric measurements.

> **Tip**: Use `STDEVA` when logical values and text need to be factored into the standard deviation calculation. For
> strict numeric analysis, switch to `STDEV.S` or `STDEV.P`.