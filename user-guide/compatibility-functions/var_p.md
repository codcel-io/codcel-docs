<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VARP Function

The `VARP` function in Excel is used to calculate the variance for an entire population of numeric data.
Variance measures how far each number in the dataset is from the mean (average) and is often used in statistics to
analyze data spread.

### Key Features of VARP:

- Calculates the variance assuming the dataset represents the **entire population**.
- Useful for statistical analysis of data variability across a complete group.
- In modern Excel versions, `VARP` has been replaced by the `VAR.P` function for better clarity, but remains available
  for compatibility.

### Syntax:

```plaintext
VARP(number1, [number2], ...)
```

- **number1**, **number2**, ...: These are the numeric values, cell ranges, or arrays forming the population data.
    - Non-numeric values within a range are ignored.
    - Up to 30 arguments can be used in older Excel versions; newer versions allow more.

### Example:

1. **Calculating Variance**  
   For the dataset `{10, 12, 23, 23, 16}`, calculate the variance of the population.  
   Formula:  
   `=VARP(10, 12, 23, 23, 16)`  
   **Result**: `27.36`

2. **Using Cell Ranges**  
   If your data is stored in cells A1:A5 (with the same values):  
   Formula:  
   `=VARP(A1:A5)`  
   **Result**: `27.36`

### Notes:

- **Population vs. Sample**:
    - Use `VARP` to calculate variance for **entire populations**.
    - Use `VAR` or `VAR.S` for samples of the population.
- **No Variation**:
    - If the dataset contains a single value or all values are identical, the result is `0`.
- **Errors**:
    - Returns `#DIV/0!` if no numeric values are provided in the input.
    - Returns `#NUM!` for invalid or empty ranges.

### Use Cases:

- **Research and Analysis**: Understand the variability in an entire population.
- **Risk Assessment**: Analyze the degree of spread in population-level metrics.
- **Performance Measurement**: Track deviations within a complete dataset in quality control or monitoring systems.

> **Tip**: Use `VAR.P` in modern Excel versions to replace `VARP` for better compatibility with updated Excel naming
conventions.