<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STDEV.P Function

The `STDEV.P` function in Excel is used to **calculate the standard deviation of an entire population** based on
numerical data. Standard deviation measures the dispersion or variation of a dataset around its mean, and this function
assumes that the provided data represents the entire population (not a sample).

### Key Features of STDEV.P:

- **Measures Variation**: Indicates how spread out the data is around the mean.
- **Entire Population**: Designed for use when the dataset includes the full population.
- **Statistical Analysis**: Commonly used for understanding data distribution in descriptive statistics.

### Syntax:

```plaintext
STDEV.P(number1, [number2], …)
```

- **number1**: Required. The first number, cell reference, or range in your dataset.
- **number2, …**: Optional. Additional numbers, cell references, or ranges containing data (up to 254 arguments).

### How It Works:

The formula for population standard deviation is:

```plaintext
σ = √[Σ(xᵢ - μ)² / N]
```

Where:

- **σ** is the population standard deviation.
- **xᵢ** is each individual data value.
- **μ** is the mean of the dataset.
- **N** is the total number of data points in the population.

The function computes this directly for the input data.

### Examples:

1. **Simple Population Standard Deviation**:
   Consider a dataset `{10, 20, 30, 40, 50}`. To calculate the population standard deviation:
   ```excel
   =STDEV.P(10, 20, 30, 40, 50)
   ```
   Result: `14.14`.

2. **Data in a Range**:
   If the dataset is in cells `A1:A5`, the formula:
   ```excel
   =STDEV.P(A1:A5)
   ```
   Yields the same result as above if `10, 20, 30, 40, 50` are in those cells.

3. **Multiple Ranges**:
   To calculate the standard deviation across multiple ranges, like `A1:A5` and `B1:B5`:
   ```excel
   =STDEV.P(A1:A5, B1:B5)
   ```

### Comparisons with Related Functions:

- **`STDEV.P` vs `STDEV.S`**:
    - Use `STDEV.P` when dealing with the **entire population**.
    - Use `STDEV.S` when the data represents a **sample** of the population, as it applies Bessel’s correction (dividing
      by `n-1` instead of `n`).

### Notes:

- **Data Type Requirements**:
    - Inputs must be numeric values or cell ranges containing numbers.
    - Non-numeric values (e.g., text, logical values) in cell references are ignored.
- **Errors**:
    - `#DIV/0!` occurs if there are no valid numeric arguments.
    - `#VALUE!` occurs if non-numeric arguments are provided without using a valid cell reference.

### Applications:

- **Descriptive Statistics**: Useful for summarizing data distributions.
- **Risk Analysis**: Analyze how data varies around its mean in fields such as finance.
- **Quality Control**: Measure consistency in manufacturing or other processes.
- **Probability Analysis**: Understand data variability when modeling entire populations.

> **Tip**: For a sample-based dataset, use `STDEV.S` instead of `STDEV.P` to avoid underestimating standard deviation.