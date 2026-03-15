<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## STANDARDIZE Function

The `STANDARDIZE` function in Excel is used to **return a normalized value (z-score)** from a given distribution. It
calculates how far a certain value is from the mean of a dataset, measured in terms of standard deviations. This
function is particularly useful for statistical analysis and comparison between datasets of different scales.

### Key Features of STANDARDIZE:

- **Normalization**: It standardizes a value in a dataset by converting it to a z-score.
- **Scale-Invariant**: Allows for comparison across datasets with different units or scales.
- **Statistical Applications**: Frequently used in statistics for normalization, regression analysis, or hypothesis
  testing.

### Syntax:

```plaintext
STANDARDIZE(x, mean, standard_dev)
```

- **x**: Required. The value you want to standardize.
- **mean**: Required. The arithmetic mean of the dataset.
- **standard_dev**: Required. The standard deviation of the dataset.

### How It Works:

The formula for standardization in Excel is:

```plaintext
z = (x - mean) / standard_dev
```

Where:

- **x** is the value being normalized.
- **mean** is the average of the dataset.
- **standard_dev** is the standard deviation of the dataset.

The result is a z-score that tells you how many standard deviations the value `x` is away from the mean.

### Examples:

1. **Basic Example**:
   Suppose the mean of a dataset is `50`, the standard deviation is `10`, and you want to standardize the value `70`:
   ```excel
   =STANDARDIZE(70, 50, 10)
   ```
   Result: `2` (The value `70` is 2 standard deviations above the mean).

2. **Negative Z-Score**:
   For a value below the mean, such as `40`:
   ```excel
   =STANDARDIZE(40, 50, 10)
   ```
   Result: `-1` (The value `40` is 1 standard deviation below the mean).

3. **Dataset Comparison**:
   If you have two employees’ test scores from different departments scaled differently:
    - Employee A: Test score = `85`, Dataset mean = `70`, Std Dev = `10`.
    - Employee B: Test score = `190`, Dataset mean = `200`, Std Dev = `15`.

   Normalize both to understand who performed better in their respective test:
   ```excel
   =STANDARDIZE(85, 70, 10)  // Employee A
   =STANDARDIZE(190, 200, 15)  // Employee B
   ```
   Results: `1.5` for Employee A and `-0.67` for Employee B.

   Interpretation: Employee A performed 1.5 standard deviations above their group’s mean, whereas Employee B scored
   below their group’s mean.

### Notes:

- **Data Requirements**:
    - The `mean` and `standard_dev` must be numeric values.
    - `standard_dev` must be greater than `0`. If `standard_dev = 0`, Excel will return a `#DIV/0!` error.
- **Other Functionality**:
    - The result from `STANDARDIZE` can be used as input for probabilities, charts, or further calculations.
- **Common Errors**:
    - `#DIV/0!`: Occurs if `standard_dev = 0`.
    - `#VALUE!`: Occurs if non-numeric arguments are provided.

### Applications:

- **Statistical Analysis**: Identify how extreme a value is in a dataset.
- **Comparing Datasets**: Useful when comparing scores or metrics from different scales.
- **Probability and Risk Analysis**: Standard scores are essential in probability and hypothesis testing.
- **Machine Learning**: Prepare data for algorithms that require normalized input.

> **Tip**: Combine `STANDARDIZE` with other statistical functions like `NORM.S.DIST` for calculating probabilities using
the standard normal distribution.