<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STDEVPA Function

The `STDEVPA` function in Excel is used to **calculate the standard deviation of an entire population**, evaluating both
numeric and non-numeric data. Unlike `STDEV.P`, this function includes logical values and text in its calculations,
assigning specific numeric values to them (e.g., `TRUE` as `1` and `FALSE` or text as `0`).

### Key Features of STDEVPA:

- **Measures Variation**: Indicates how spread out the population data is around its mean.
- **Handles Mixed Data Types**: Evaluates logical values and text alongside numbers.
- **Population-Based Calculation**: Uses the population standard deviation formula (divides by `N`), designed for entire
  population datasets.

### Syntax:

```plaintext
STDEVPA(value1, [value2], …)
```

- **value1**: Required. The first value, cell reference, or range to evaluate.
- **value2, …**: Optional. Additional values, cell references, or ranges (up to 254 arguments).

### How It Works:

The formula for population standard deviation is:

```plaintext
σ = √[Σ(xᵢ - μ)² / N]
```

Where:

- **xᵢ** is each individual data point (including treated logical and text values).
- **μ** is the population mean.
- **N** is the total number of data points in the population.

### Data Evaluation Rules:

For non-numeric data in the input:

- **Logical Values**:
    - `TRUE` is treated as `1`.
    - `FALSE` is treated as `0`.
- **Text**:
    - Any text (even numbers entered as text) is treated as `0`.

### Examples:

1. **Simple Calculation with Mixed Types**:
   Consider the dataset `{10, TRUE, FALSE, "text", 30}`. To calculate the population standard deviation:
   ```excel
   =STDEVPA(10, TRUE, FALSE, "text", 30)
   ```
    - Logical values are treated as `1` (TRUE) and `0` (FALSE).
    - Text is treated as `0`.
    - Converted dataset: `{10, 1, 0, 0, 30}`.
    - Mean: `(10 + 1 + 0 + 0 + 30) / 5 = 8.2`.
    - Result: `11.56`.

2. **Using Cell Ranges**:
   If the dataset is in cells `A1:A5` with values `{10, TRUE, FALSE, "text", 30}`, the formula:
   ```excel
   =STDEVPA(A1:A5)
   ```
   Yields the same result as above.

3. **Combination of Ranges and Values**:
   For a dataset spread across `A1:A3` and `{20, FALSE}` as additional values:
   ```excel
   =STDEVPA(A1:A3, 20, FALSE)
   ```

### Comparisons with Related Functions:

- **`STDEVPA` vs `STDEV.P`**:
    - `STDEVPA` includes logical values and text in calculations.
    - `STDEV.P` ignores logical values and text.

- **`STDEVPA` vs `STDEVA`**:
    - Both include logical values and text in calculations.
    - `STDEVPA` calculates population standard deviation (divides by `N`).
    - `STDEVA` calculates sample standard deviation (divides by `n-1`).

- **`STDEVPA` vs `VARPA`**:
    - Both include all data types and use population-based calculations.
    - `STDEVPA` returns the standard deviation; `VARPA` returns the variance (the square of the standard deviation).

### Notes:

- **Data Type Inclusion**:
    - Use `STDEVPA` when logical values and text are intentionally part of the dataset and the data represents an entire
      population.
    - Inputs that are empty cells are ignored.
- **Errors**:
    - `#DIV/0!` occurs if there are no valid data points after evaluation (e.g., all empty cells).
- **Performance Tip**:
    - When dealing exclusively with numbers, prefer `STDEV.P` for faster computation.

### Applications:

- **Mixed Datasets**: Analyze variation in population datasets with a mix of numeric and logical/text values.
- **Survey Data**: Calculate variability in complete survey results where responses include `TRUE`/`FALSE` or text.
- **Census Data**: Assess entire population datasets containing both qualitative and numeric measurements.

> **Tip**: Use `STDEVPA` when logical values and text need to be factored into the standard deviation calculation for an
> entire population. For sample-based analysis with mixed data types, use `STDEVA` instead.