<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STDEVP Function

The `STDEVP` function in Excel is used to calculate the standard deviation for an entire population of numeric data.
Standard deviation is a measure that indicates how much the values in a dataset vary from the mean (average).

### Key Features of STDEVP:

- Calculates the spread of data assuming the dataset represents the **entire population**.
- Useful for statistical analysis of variability within large datasets.
- Replaced in modern Excel versions by the `STDEV.P` function for clarity, but still available for compatibility.

### Syntax:

```plaintext
STDEVP(number1, [number2], ...)
```

- **number1**, **number2**, ...: These are the numeric values, cell ranges, or arrays forming the population data.
    - Non-numeric values within a range are ignored.
    - You can use up to 30 arguments in older Excel versions; newer versions allow more.

### Example:

1. **Calculating Standard Deviation**  
   Suppose you have the dataset `{10, 12, 23, 23, 16}` and want to calculate the standard deviation of the population.  
   Formula:  
   `=STDEVP(10, 12, 23, 23, 16)`  
   **Result**: `5.71277`

2. **Using Cell Ranges**  
   If your data is stored in cells A1:A5 (with the same values):  
   Formula:  
   `=STDEVP(A1:A5)`  
   **Result**: `5.71277`

### Notes:

- **Population vs. Sample**:
    - Use `STDEVP` for an **entire population**.
    - Use `STDEV` or `STDEV.S` for **samples of the population**.
- **No Variation**:
    - If the dataset contains a single value or all values are identical, the result is `0`.
- **Errors**:
    - The function returns `#DIV/0!` if no numeric values are provided in the input.
    - Returns `#NUM!` for invalid or empty ranges.

### Use Cases:

- **Research and Analysis**: Measure population-level data variation.
- **Finance and Risk Management**: Assess the volatility across an entire period or group of data points.
- **Manufacturing**: Identify consistency and spread in production quality.

> **Tip**: Use `STDEV.P` in modern Excel to replace `STDEVP` for improved compatibility with updated standards.