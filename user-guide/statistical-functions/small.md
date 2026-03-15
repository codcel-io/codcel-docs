<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

1## SMALL Function

The `SMALL` function in Excel is used to **return the k-th smallest value** in a dataset. This function is particularly
useful when you want to determine specific ranking elements within a range, such as the smallest, second smallest, etc.

### Key Features of SMALL:

- **Find Smallest Values**: You can retrieve the smallest `k` values in a numeric dataset by specifying the desired
  position (`k`).
- **Ranking**: It allows you to select values based on their order, starting from the smallest.
- **Flexible Usage**: Useful for filtering datasets or identifying low-value thresholds.

### Syntax:

```plaintext
SMALL(array, k)
```

- **array**: Required. The range or array of numeric values from which you want to find the `k-th` smallest value.
- **k**: Required. An integer specifying the position of the smallest value to return, where:
    - `k = 1` returns the smallest value,
    - `k = 2` returns the second smallest value, and so on.

### How It Works:

The `SMALL` function orders the values in the specified array in ascending order and then picks the value at the
specified position (`k`).

### Examples:

1. **Basic Example**:
   Suppose you have the following dataset in cells `A1:A5`: `{10, 20, 5, 25, 15}`. To find the **smallest value**:
   ```excel
   =SMALL(A1:A5, 1)
   ```
   Result: `5` (The smallest value in the range).

2. **Second Smallest Value**:
   To find the **second smallest value** in the same dataset:
   ```excel
   =SMALL(A1:A5, 2)
   ```
   Result: `10`.

3. **Larger k Value**:
   To find the **fourth smallest value**:
   ```excel
   =SMALL(A1:A5, 4)
   ```
   Result: `20`.

4. **Dynamic Example**:
   If you have a dataset `{8, 3, 12, 5, 7}` and want the user to input the ranking dynamically into cell `B1` (e.g.,
   `k = 3`):
   ```excel
   =SMALL(A1:A5, B1)
   ```
   Result: Corresponds to the value at the position input by the user.

### Notes:

- **Data Requirements**:
    - The function only works with numeric values. Any non-numeric values in the array will be ignored.
    - If `k` is less than 1 or greater than the total number of elements in the array, Excel returns a `#NUM!` error.

- **Other Functionality**:
    - Use `LARGE` to find the `k-th` **largest** value in a dataset (opposite of `SMALL`).
    - Combine with other functions, such as `IF` or `INDEX`, for more complex conditional operations.

- **Common Errors**:
    - `#NUM!`: Occurs when `k` is out of range (e.g., `k > count(array)` or `k < 1`).
    - `#VALUE!`: Occurs if `k` is non-numeric.

### Applications:

- **Data Analysis**: Identify smallest values, such as minimum expenses or the shortest time in performance metrics.
- **Filtering & Thresholds**: Highlight data below certain thresholds in large datasets.
- **Statistical Calculations**: Find quartiles or other relative positions within datasets (e.g., smallest 25% or worst
  10%).

> **Tip**: Pair the `SMALL` function with conditional formatting to visually identify small values or use it with
`INDEX` to find the corresponding entry for a specific rank.