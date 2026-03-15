<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RANK.AVG Function

The `RANK.AVG` function in Excel is used to **determine the rank of a number in a dataset**, but unlike the `RANK.EQ`
function, it assigns an average rank if multiple numbers have the same value (i.e., ties). This function is particularly
helpful when analyzing numeric data and creating ranked lists while accounting for ties in a fair manner.

### Key Features of RANK.AVG:

- **Ranking a Dataset**: Provides the rank of a specific value relative to other values in a dataset.
- **Average Rank Handling**: In cases of ties, the function assigns an average rank to the tied values.
- **Customizable Order**: You can determine whether to rank in ascending or descending order.

### Syntax:

```plaintext
RANK.AVG(number, ref, [order])
```

- **number**: Required. The number whose rank you want to determine.
- **ref**: Required. The range or array of numbers to evaluate.
- **order**: Optional. A numeric value to specify the ranking order:
    - `0` or omitted: Ranks in descending order (largest-to-smallest).
    - `1`: Ranks in ascending order (smallest-to-largest).

### How It Works:

The function compares the **number** to all other values in the specified range (**ref**) and determines its rank based
on the order:

- **Descending Order** (default):
    - A higher number gets a lower rank (rank 1 is the largest).
- **Ascending Order**:
    - A lower number gets a lower rank (rank 1 is the smallest).

If two or more values are identical (tie), `RANK.AVG` assigns them the average rank of those positions in the order.

### Examples:

1. **Descending Order (Default)**:
   To rank the number `10` in the dataset `{15, 20, 10, 10, 8, 5, 25}` in descending order:
   ```excel
   =RANK.AVG(10, {15, 20, 10, 10, 8, 5, 25})
   ```
   Result: `5.5` (The two `10`s are tied, so their rank is the average of 5th and 6th positions: `(5 + 6)/2 = 5.5`).

2. **Ascending Order**:
   To rank the number `10` in the same dataset in ascending order:
   ```excel
   =RANK.AVG(10, {15, 20, 10, 10, 8, 5, 25}, 1)
   ```
   Result: `3.5` (Average rank of 3rd and 4th positions when ranked smallest-to-largest).

3. **Without Ties**:
   To calculate the rank of a unique value, such as `25`:
   ```excel
   =RANK.AVG(25, {15, 20, 10, 10, 8, 5, 25})
   ```
   Result: `1` (As `25` is the largest in descending order).

### Notes:

- **Handling Non-Numeric Data**:
    - The function ignores non-numeric values in the dataset.
    - Passing non-numeric values as **number** results in a `#VALUE!` error.
- **Error Conditions**:
    - `#N/A`: If the **number** does not exist in the dataset.
    - `#VALUE!`: If an invalid type is passed for **order**.
- **Sorting Impact**:
    - The dataset (**ref**) doesn't need to be sorted manually — the function handles sorting internally.
- **Tiebreaker Calculations**:
    - The average rank for ties ensures fair rankings in statistical and competitive contexts.

### Applications:

- **Ranking Competitors**: Accounting for ties in sports or academic rankings.
- **Statistical Analysis**: Identifying percentile or rank-based trends in datasets.
- **Financial Comparisons**: Ranking companies, individuals, or investments by performance.
- **Data Reporting**: Displaying ordered datasets while properly managing duplicate values.

> **Tip**: Use `RANK.EQ` when ties should not result in averaged rankings, or when ranking speed is a priority and
averaging is unnecessary.