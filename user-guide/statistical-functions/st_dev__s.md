<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STDEV.S Function

The `STDEV.S` function in Excel is used to **calculate the standard deviation of a sample** based on numerical data.
Standard deviation measures the dispersion or variation of a dataset around its mean, and this function applies Bessel's
correction (dividing by `n-1`), which accounts for the fact that the dataset is a sample of the population.

### Key Features of STDEV.S:

- **Measures Variation**: Indicates how spread out the sample data is around its mean.
- **Sample-Based Calculation**: Designed for use when the dataset represents a sample of a larger population.
- **Statistical Analysis**: Commonly used for inferring population statistics from a sample.

### Syntax:

```plaintext
STDEV.S(number1, [number2], …)
```

- **number1**: Required. The first number, cell reference, or range in your dataset.
- **number2, …**: Optional. Additional numbers, cell references, or ranges containing data (up to 254 arguments).

### How It Works:

The formula for sample standard deviation is:

```plaintext
s = √[Σ(xᵢ - x̄)² / (n - 1)]
```

Where:

- **s** is the sample standard deviation.
- **xᵢ** is each individual data value.
- **x̄** is the sample mean.
- **n** is the total number of data points in the sample.

The function computes this directly for the input data.

### Examples:

1. **Simple Sample Standard Deviation**:
   Consider a sample dataset `{10, 20, 30, 40, 50}`. To calculate the sample standard deviation:
   ```excel
   =STDEV.S(10, 20, 30, 40, 50)
   ```
   Result: `15.81`.

2. **Data in a Range**:
   If the sample dataset is in cells `A1:A5`, the formula:
   ```excel
   =STDEV.S(A1:A5)
   ```
   Yields the same result as above if `10, 20, 30, 40, 50` are in those cells.

3. **Multiple Ranges**:
   To calculate the sample standard deviation across multiple ranges, like `A1:A5` and `B1:B5`:
   ```excel
   =STDEV.S(A1:A5, B1:B5)
   ```

### Comparisons with Related Functions:

- **`STDEV.S` vs `STDEV.P`**:
    - Use `STDEV.S` when the dataset is a **sample** of the population.
    - Use `STDEV.P` when the dataset includes the **entire population**, as there is no need for Bessel's correction.

### Notes:

- **Data Type Requirements**:
    - Inputs must be numeric values or cell ranges containing numbers.
    - Non-numeric values (e.g., text, logical values) in cell references are ignored.
- **Errors**:
    - `#DIV/0!` occurs if there are fewer than two valid numeric arguments.
    - `#VALUE!` occurs if non-numeric arguments are provided without valid cell references.

### Applications:

- **Descriptive Statistics**: Useful for summarizing variability in sample data.
- **Inference**: Estimating properties of a population from sample data.
- **Risk Analysis**: Analyze variability within a sample when modeling possible outcomes.
- **Quality Control**: Measure variation in samples during manufacturing or testing.

> **Tip**: Use `STDEV.S` for analyzing data samples to ensure accurate variability estimates. For population-level data,
> choose `STDEV.P` instead.