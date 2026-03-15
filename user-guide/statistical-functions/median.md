<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MEDIAN Function

The `MEDIAN` function in Excel is used to **calculate the median or the middle value** of a set of numbers. The median
is the value that separates the higher half and the lower half of the dataset when it is sorted in ascending order. If
the dataset has an even number of values, the `MEDIAN` function returns the average of the two middle numbers.

### Key Features of MEDIAN:

- **Removes Outliers**: The median is less affected by extreme values or outliers than the mean.
- Can handle numbers, ranges, or arrays.
- Works with datasets containing both positive and negative values, as well as zeros.

### Syntax:

```plaintext
MEDIAN(number1, [number2], ...)
```

- **number1**: Required. The first number, range, or array in the dataset.
- **number2,...**: Optional. Additional numbers, ranges, or arrays (up to 255 values) to include in the dataset.

### How It Works:

1. The function sorts the numbers in ascending order internally.
2. It identifies the middle value:
    - For an odd count of numbers: Returns the single middle value.
    - For an even count of numbers: Returns the average of the two middle values.

### Examples:

1. **Basic Median Calculation**:
   ```excel
   =MEDIAN(1, 3, 5, 7, 9)
   ```
   Result: `5` (middle value of the sorted data `{1, 3, 5, 7, 9}`).

2. **Even Number of Values**:
   ```excel
   =MEDIAN(2, 4, 6, 8)
   ```
   Result: `5` (average of the two middle values, `4` and `6`).

3. **Using a Range of Numbers**:
   Suppose the cells A1:A5 contain `{12, 15, 7, 10, 9}`:
   ```excel
   =MEDIAN(A1:A5)
   ```
   Result: `10` (middle value of the sorted dataset `{7, 9, 10, 12, 15}`).

4. **Including Negative Numbers**:
   ```excel
   =MEDIAN(-5, -1, 0, 3, 7)
   ```
   Result: `0` (middle value of the dataset).

5. **Handling Mixed Data**:
   The function ignores non-numeric values while calculating:
   ```excel
   =MEDIAN(10, "text", 20, 30)
   ```
   Result: `20` (ignores `"text"`).

### Notes:

- **Text and Logical Values in Ranges**:
    - When providing a range, `MEDIAN` ignores text and logical values.
    - However, if logical values (e.g., `TRUE`, `FALSE`) are entered directly as arguments, they are evaluated as `1`
      and `0`, respectively.
    ```excel
    =MEDIAN(TRUE, FALSE, 5)
    ```
  Result: `1` (dataset transformed to `{1, 0, 5}`).

- **Empty Cells**:
    - Empty cells in ranges are ignored, but zeros are included.

- **Error Values**:
    - If an error value exists in the dataset, the function returns that error.

### Applications:

- **Data Analysis**: Obtain a central value from a dataset unaffected by extreme outliers.
- **Statistical Modeling**: Compare the median with other measures like mean and mode to analyze data distribution.
- **Financial Calculations**: Assess typical values in time-series data like salary distributions or stock prices.

> **Tip:** Use `MEDIAN` combined with `COUNT` and `AVERAGE` to analyze statistical properties of your data thoroughly.