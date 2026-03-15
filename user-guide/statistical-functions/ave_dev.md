<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## AVEDEV Function

The `AVEDEV` function in Excel calculates the **average of the absolute deviations** of data points from their mean.
This function is often used in statistical analysis to measure the dispersion or variability of data.

Mathematically, it can be expressed as:

    AVEDEV = (|x₁ - μ| + |x₂ - μ| + ... + |xₙ - μ|) / n

where:

- `x₁, x₂, ..., xₙ` are the data points,
- `μ` is the arithmetic mean of the data set,
- `n` is the total number of data points.

It provides insight into how far each data point deviates from the average, without considering the direction of
deviation (positive or negative).

### Syntax:

    AVEDEV(number1, [number2], ...)

- **number1, [number2], ...**: These are the numbers for which you want to calculate the average absolute deviation. The
  first argument is required, while subsequent arguments are optional. You can input up to 255 numbers or ranges.

### Key Points:

- The `AVEDEV` function works with both positive and negative numbers.
- Logical values and text representations of numbers within arrays or references are evaluated (e.g., `TRUE` is treated
  as `1`, `FALSE` as `0`).
- Text or error values in the arguments will cause errors.

### Examples:

1. `=AVEDEV(5, 10, 15, 20, 25)`  
   Calculates the average of the absolute deviations of the numbers `5, 10, 15, 20, 25` from their mean.  
   **Result**: `6`

2. `=AVEDEV(A1:A5)`  
   Computes the average absolute deviation for the range `A1:A5`.

3. `=AVEDEV(10, 20, 30, "40")`  
   Treats `"40"` as `40` and calculates the average absolute deviation.  
   **Result**: `7.5`

### Notes:

- The `AVEDEV` function is particularly useful in data analysis for summarizing variability or spread, especially when
  you want a non-negative measure of dispersion.
- Ensure that the input data is valid for computation; otherwise, errors may occur.
- It's different from `STDEV` (Standard Deviation), as `AVEDEV` uses absolute deviations instead of squared deviations
  and does not measure variance.

> **Tip**: Use `AVEDEV` when you need a straightforward measure of variability that ignores the direction of
> differences. Combine it with other statistical functions, such as `MEAN` or `MODE`, for deeper analysis.