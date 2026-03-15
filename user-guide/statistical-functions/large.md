<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LARGE Function

The `LARGE` function in Excel is used to **return the k-th largest value** in a dataset. It is particularly helpful for
analyzing datasets where you need specific high-ranking values, such as the maximum number, second-largest value, etc.

### Key Features of LARGE:

- **Ranks Data**: Identifies the `k-th` largest value in the provided dataset.
- Useful when you need to extract top-most values for reporting, analysis, or comparisons.
- Works with both numeric values and ranges.

### Syntax:

```plaintext
LARGE(array, k)
```

- **array**: The dataset or range of values where you want to find the `k-th` largest value.
- **k**: The rank of the value you are looking for (e.g., `1` for the largest, `2` for the second largest, and so on).

### How It Works:

The `LARGE` function sorts the provided array in descending order and then retrieves the value based on the position (or
rank) specified by `k`.

### Examples:

1. **Basic Calculation**:

   Given the dataset `{3, 8, 5, 10, 2}`, find the 2nd largest value:
   ```excel
   =LARGE({3, 8, 5, 10, 2}, 2)
   ```
   Result: `8`

2. **Using a Range**:

   If `A1:A5` contains the dataset `{3, 8, 5, 10, 2}`, find the largest value:
   ```excel
   =LARGE(A1:A5, 1)
   ```
   Result: `10`

3. **Top 3 Values**:

   To find the top 3 values in the range `B1:B10`:
    - First-largest value:
      ```excel
      =LARGE(B1:B10, 1)
      ```
    - Second-largest value:
      ```excel
      =LARGE(B1:B10, 2)
      ```
    - Third-largest value:
      ```excel
      =LARGE(B1:B10, 3)
      ```

4. **Dynamic Analysis with Helper Functions**:

   Find the second-largest sales amount, where `C1:C10` stores monthly sales figures:
   ```excel
   =LARGE(C1:C10, 2)
   ```

### Notes:

- **Parameter Constraints**:
    - The value of `k` must be a positive integer and less than or equal to the number of data points in the array.
      Otherwise, you will get a `#NUM!` error.
    - Blank cells, text, or logical values (`TRUE`/`FALSE`) inside the array are ignored.

- **Special Cases**:
    - If all the numbers in the array are identical, the result will always be the repeated value, regardless of `k`.

### Applications:

- **Data Analysis**: Extract the highest or nth-highest value from datasets for meaningful insights.
- **Finance**: Identify and analyze the top transactions, expenses, or profits.
- **Sports Analytics**: Rank athletes or teams by performance metrics (e.g., fastest run times, highest scores).
- **Quality Monitoring**: Determine the highest defect count or production output to take corrective actions.

> **Tip:** Combine `LARGE` with other functions like `IF`, `AVERAGE`, or `INDEX` to perform more advanced analyses and
handle conditional rankings. For instance, use it alongside `SMALL` to analyze both the largest and smallest values in a
dataset.