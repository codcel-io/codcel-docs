<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RANK Function

The `RANK` function in Excel is used to determine the rank of a number within a dataset. The rank represents the
position of a number relative to other numbers in the dataset, either in ascending or descending order.

### Key Features of RANK:

- Determines the rank of a number in a list of numbers.
- Useful for analyzing relative standings or positions within datasets.
- The updated equivalent function in modern Excel is `RANK.EQ`.

### Syntax:

```plaintext
RANK(number, ref, [order])
```

- **number**: The number whose rank you want to determine.
- **ref**: The range of numbers in which to rank the number.
- **order** *(optional)*:
    - `0` or omitted: Ranks numbers in descending order (largest number is ranked `1`).
    - `1`: Ranks numbers in ascending order (smallest number is ranked `1`).

### Example:

1. **Ranking in Descending Order**  
   Suppose you have the dataset `{10, 20, 30, 40, 50}` and want to find the rank of `30`:  
   Formula:  
   `=RANK(30, {10, 20, 30, 40, 50})`  
   **Result**: `3` (30 is the 3rd largest number).

2. **Ranking in Ascending Order**  
   Using the same dataset but sorting in ascending order:  
   Formula:  
   `=RANK(30, {10, 20, 30, 40, 50}, 1)`  
   **Result**: `3` (30 is the 3rd smallest number).

### Notes:

- **Behavior**:
    - The function assigns the same rank to duplicate numbers but skips the subsequent ranks (i.e., ties are assigned
      the same rank).
    - It automatically handles datasets without needing manual sorting.
- **Invalid Inputs**:
    - If `number` is not found in the `ref` range, Excel returns a `#N/A` error.
    - If `ref` contains non-numeric values, Excel ignores them during ranking.

### Use Cases:

- **Data Analysis**: Identify rankings or standings of elements in datasets.
- **Comparison of Data Points**: Evaluate the relative performance of values.
- **Team or Group Performance**: Determine ranking among participants or groups.

> **Note**: The `RANK` function is supported for legacy purposes but has been replaced by `RANK.EQ` and `RANK.AVG` in
modern Excel functions.