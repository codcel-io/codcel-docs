<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MODE.SNGL Function

The `MODE.SNGL` function in Excel is used to **find the single most frequently occurring value (mode)** in a dataset.  
Unlike the `MODE.MULT` function, `MODE.SNGL` only returns one mode, even if multiple modes exist.

### Key Features of MODE.SNGL:

- Returns the most frequent value in a dataset.
- Works with numbers, ranges, or arrays.
- If no value repeats, the function returns an error (`#N/A`).

### Syntax:

```plaintext
MODE.SNGL(number1, [number2], ...)
```

- **number1**: Required. The first numeric value, cell reference, or range to evaluate.
- **number2,...**: Optional. Additional numeric values, cell references, or ranges (up to 255) to include in the
  dataset.

### How It Works:

1. The function evaluates the frequency of each number in the dataset.
2. It identifies the value that occurs most frequently.
3. If there is a tie, it only returns the **first mode it encounters**.

### Examples:

1. **Basic Example**:
   ```excel
   =MODE.SNGL(1, 2, 2, 3, 3, 4)
   ```
   Result: `2` (the first most frequent number found).

2. **Using Cell Ranges**:
   Suppose the cells A1:A6 contain `{1, 2, 2, 3, 3, 4}`:
   ```excel
   =MODE.SNGL(A1:A6)
   ```
   Result: `2`.

3. **Find Mode in a Single-Mode Dataset**:
   ```excel
   =MODE.SNGL(5, 1, 2, 5, 3, 5)
   ```
   Result: `5` (only one mode exists: `5`).

4. **No Repeating Values**:
   ```excel
   =MODE.SNGL(1, 2, 3, 4, 5)
   ```
   Result: `#N/A` (no number repeats in the dataset).

5. **Dataset with Ties**:
   In a dataset where `{2, 3}` occur equally often (e.g., `{1, 2, 2, 3, 3, 4}`):
   ```excel
   =MODE.SNGL(A1:A6)
   ```
   Result: `2` (the first mode the function encounters).

### Notes:

- **Behavior with Text and Logical Values**:
    - Text and logical values are ignored. For example:
    ```excel
    =MODE.SNGL(1, 2, "text", FALSE, 2, 3)
    ```
  Result: `2`.

- **Error Handling**:
    - If an error exists in the dataset, the function returns that error.

- **Older Versions**:
    - In versions prior to Excel 2010, use the `MODE` function (which works the same as `MODE.SNGL`).

### Applications:

- **Statistical Analysis**: Quickly identify the most common value in a dataset.
- **Inventory Management**: Analyze the most frequently used or sold item.
- **Data Quality Checks**: Spot inconsistencies or frequently recurring outliers.

> **Tip:** For datasets with multiple modes, use `MODE.MULT` to return all modes.