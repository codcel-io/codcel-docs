<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->


## RANK.EQ Function

The `RANK.EQ` function in Excel is used to **determine the rank of a number in a dataset**, ensuring that tied values 
receive the same rank. This function is beneficial when analyzing numeric data and ranking values in a dataset, 
especially when ties are acceptable without needing an averaged rank.

### Key Features of RANK.EQ:

- **Ranking a Dataset**: Provides the rank of a specific value relative to other values in a dataset.
- **Tie Handling**: Assigns the same rank to tied values without averaging.
- **Customizable Order**: Supports ranking in ascending or descending order.

### Syntax:

```plaintext
RANK.EQ(number, ref, [order])
```

- **number**: Required. The number whose rank you want to determine.
- **ref**: Required. The range or array of numbers to evaluate.
- **order**: Optional. A numeric value to specify the ranking order:
  - `0` or omitted: Ranks in descending order (largest-to-smallest).
  - `1`: Ranks in ascending order (smallest-to-largest).

### How It Works:

The function evaluates the **number** against all values in the specified range (**ref**) and assigns a rank according to the order:

- **Descending Order** (default):
  - Higher numbers are ranked lower numerically (rank 1 is the largest).
- **Ascending Order**:
  - Lower numbers are ranked lower numerically (rank 1 is the smallest).

If two or more numbers in the dataset have the same value (a tie), `RANK.EQ` assigns them the same rank. In descending order, larger numbers have higher ranks, and vice versa for ascending order.

### Examples:

1. **Descending Order (Default)**:
   To rank the number `10` in the dataset `{15, 20, 10, 10, 8, 5, 25}` in descending order:
   ```excel
   =RANK.EQ(10, {15, 20, 10, 10, 8, 5, 25})
   ```
   Result: `5` (Both `10`s share the same rank).

2. **Ascending Order**:
   To rank the number `10` in the same dataset in ascending order:
   ```excel
   =RANK.EQ(10, {15, 20, 10, 10, 8, 5, 25}, 1)
   ```
   Result: `3` (Both `10`s share the same rank in smallest-to-largest ordering).

3. **Unique Value**:
   To calculate the rank of a unique value, such as `25`:
   ```excel
   =RANK.EQ(25, {15, 20, 10, 10, 8, 5, 25})
   ```
   Result: `1` (As `25` is the largest value in descending order).

### Notes:

- **Exclusion of Non-Numeric Values**:
  - The function ignores non-numeric values in the dataset.
  - If **number** is non-numeric, it results in a `#VALUE!` error.
- **Error Handling**:
  - `#N/A`: Returned if the **number** does not exist in the dataset.
  - `#VALUE!`: Returned if an invalid type is passed as the **order** argument.
- **Dataset Order**: 
  - The dataset (**ref**) does not need to be sorted since the function internally organizes and evaluates the values.
  
### Applications:

- **Ranking Competitors**: Useful for competitions or rankings where tied scores receive equal standing.
- **Statistics and Analysis**: Quickly determine positional trends in lists based on order.
- **Business Analytics**: Rank products, services, or employee performance based on numeric metrics.
- **Data Reporting**: Assist in formatting ranked data for presentations or insights.

> **Tip**: Use `RANK.AVG` when tied ranks should be averaged,