<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PERCENTRANK Function

The `PERCENTRANK` function in Excel is used to determine the **relative rank of a value** within a dataset as a
percentage. It calculates where a specific value stands in relation to the rest of the dataset, expressed as a
percentage between **0** and **1**, inclusive.

### Key Features of PERCENTRANK:

- Returns the rank of a value as a percentage of the dataset.
- Useful for statistical evaluation and comparing the relative standing of a value in a dataset.
- The updated equivalent function in modern Excel is `PERCENTRANK.INC`.

### Syntax:

```plaintext
PERCENTRANK(array, x, [significance])
```

- **array**: The range or array of values that defines the dataset in which to calculate the percentage rank.
- **x**: The specific value whose percentage rank you want to determine.
- **significance**: *(Optional)* The number of significant digits to display in the result. If omitted, Excel uses three
  significant digits by default.

### Example:

1. **Finding the Percent Rank of a Value in a Dataset**  
   Suppose you have the dataset `{10, 20, 30, 40, 50}` and want to calculate the percentage rank for the value `30`:  
   Formula:  
   `=PERCENTRANK({10,20,30,40,50}, 30)`  
   **Result**: `0.5` (meaning `30` is at the 50th percentile in the dataset).

2. **Specifying the Number of Significant Digits**  
   Using the same dataset and value, but now specifying **5 significant digits**:  
   Formula:  
   `=PERCENTRANK({10,20,30,40,50}, 30, 5)`  
   **Result**: `0.50000`

### Notes:

- **Output**:
    - The result is a fraction between **0 and 1**, where:
        - `0` corresponds to the smallest value in the dataset.
        - `1` corresponds to the largest value in the dataset.
        - Intermediate results represent the proportion of values smaller than the given value.
    - The result can also be displayed as a percentage by formatting the cell appropriately.
- **Invalid inputs**:
    - If the `x` value does not exist in the dataset and cannot be interpolated, Excel returns a `#N/A` error.
    - If the dataset (`array`) is empty, Excel returns a `#NUM!` error.
- Interpolation is applied by Excel if the `x` value falls between two values in the dataset, meaning the function can
  estimate a rank even for non-exact matches.
- **Non-Inclusive Percentages**:
    - If you want strictly **exclusive percentile values** (excluding `0` and `1`), use the related `PERCENTRANK.EXC`
      function.

### Use Cases:

- **Performance Evaluation**: Assess an individual's or entity's standing relative to a group or dataset.
- **Data Analysis**: Compare data points within a range and identify their relative standings.
- **Statistical Scoring**: Translate raw scores into relative scores for normalization in studies or evaluations.

> **Note**: The `PERCENTRANK` function is still supported for backward compatibility but has been replaced by the
`PERCENTRANK.INC` function, which is more consistent with modern naming standards.