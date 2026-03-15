<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MODE Function

The `MODE` function in Excel is used to **find the most frequently occurring value** in a dataset. If multiple values
are tied as the most frequent, the `MODE` function returns the first one it encounters. This makes it especially useful
for identifying common patterns or trends in numerical data.

### Key Features of MODE:

- **Handles Frequencies**: Returns the number or value that occurs the most in the dataset.
- Can process numbers or arrays with multiple values.
- If no value appears more than once, the result is an error (`#N/A`).

### Syntax:

```plaintext
MODE(number1, [number2], ...)
```

- **number1**: Required. The first number, range, or array in the dataset.
- **number2,...**: Optional. Additional numbers, ranges, or arrays (up to 255 values).

### How It Works:

1. The function scans through the dataset to count the frequency of each value.
2. It identifies the value that occurs the most number of times.
3. If all values are unique (no repetition), it returns `#N/A`.

> **Note:** Newer Excel versions replace the `MODE` function with `MODE.SNGL` and `MODE.MULT`, but `MODE` is still
> available for backward compatibility.

### Examples:

1. **Basic Mode Calculation**:
   ```excel
   =MODE(1, 2, 2, 3, 4)
   ```
   Result: `2` (since `2` occurs more than any other number).

2. **Using a Range of Numbers**:
   Suppose the cells A1:A6 contain `{4, 7, 4, 6, 4, 5}`:
   ```excel
   =MODE(A1:A6)
   ```
   Result: `4` (most frequent value in the range).

3. **No Repeated Values**:
   ```excel
   =MODE(1, 2, 3, 4, 5)
   ```
   Result: `#N/A` (no number is repeated).

4. **Handling Mixed Data**:
   If a range contains text or logical values, they are ignored:
   ```excel
   =MODE(10, 20, "text", 10, 30)
   ```
   Result: `10` (most frequent numerical value, ignoring `"text"`).

5. **Multiple Frequent Values**:
   If there are equal frequencies, only the first is returned:
   ```excel
   =MODE(1, 2, 2, 3, 3)
   ```
   Result: `2` (first value with the highest frequency).

### Notes:

- **Text and Logical Values**:
    - Non-numeric values in the dataset are ignored.
    - If logical values like `TRUE` and `FALSE` are entered directly as arguments, they are evaluated as `1` and `0`,
      respectively.
    ```excel
    =MODE(TRUE, FALSE, 1, 2, 1)
    ```
  Result: `1` (since both `TRUE` and the number `1` are counted as `1`).

- **Empty Cells**:
    - Empty cells in ranges are ignored.
    - Zeros are treated as valid numbers and can be part of the result.

- **Error Values**:
    - If an error value exists in the dataset, the function will return that error.

### Applications:

- **Data Analysis**: Identify the most common value in datasets such as survey responses, grades, or sales data.
- **Statistical Comparisons**: Use in conjunction with the `MEDIAN` and `AVERAGE` functions to analyze distributions.
- **Financial Reporting**: Detect trends like the most frequent transaction amount or stock price in a time period.

> **Tip:** For datasets with multiple modes, consider using `MODE.MULT` to return all the frequently occurring values.