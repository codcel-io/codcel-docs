<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MODE.MULT Function

The `MODE.MULT` function in Excel is used to **find one or more modes (most frequently occurring values)** in a dataset.
Unlike the `MODE.SNGL` function, which only returns a single mode even if multiple modes exist, `MODE.MULT` can return
all modes when the data is bimodal or multimodal.

### Key Features of MODE.MULT:

- **Supports Multimodal Data**: Identifies and returns multiple modes when they exist.
- Works with numbers, ranges, or arrays.
- If no value repeats, the function returns an error (`#N/A`).

### Syntax:

```plaintext
MODE.MULT(number1, [number2], ...)
```

- **number1**: Required. The first numeric value, cell reference, or range to evaluate.
- **number2,...**: Optional. Additional numeric values, cell references, or ranges (up to 255) to include in the
  dataset.

### How It Works:

1. The function evaluates the frequency of each number in the dataset.
2. It identifies the values that occur most frequently.
3. If there are multiple modes, it can return them as an array (when entered as an array formula).

### Examples:

1. **Basic Example**:
   ```excel
   =MODE.MULT(1, 2, 2, 3, 3, 4)
   ```
   Result: `{2, 3}` (both `2` and `3` occur most frequently).

2. **Using Cell Ranges**:
   Suppose the cells A1:A6 contain `{1, 2, 2, 3, 3, 4}`:
   ```excel
   =MODE.MULT(A1:A6)
   ```
   Result: `{2, 3}`.

3. **Find Mode in a Single-Mode Dataset**:
   ```excel
   =MODE.MULT(5, 1, 2, 5, 3, 5)
   ```
   Result: `{5}` (only one mode exists: `5`).

4. **No Repeating Values**:
   ```excel
   =MODE.MULT(1, 2, 3, 4, 5)
   ```
   Result: `#N/A` (no number repeats in the dataset).

5. **Array Output (Enter as Array)**:
   When using `MODE.MULT` to return multiple modes, you must select the range of cells where modes should appear, then
   enter the formula using **Ctrl+Shift+Enter** (in older versions of Excel):
   ```excel
   =MODE.MULT(A1:A6)
   ```
   Result: `{2, 3}` shown across two cells if the data in `A1:A6` is `{1, 2, 2, 3, 3, 4}`.

### Notes:

- **Array Behavior**:
    - In Excel 365 or Excel 2021 (with dynamic arrays), the results "spill" into adjacent cells automatically without
      requiring array formula syntax (Ctrl+Shift+Enter).
    - In older versions, you must use Ctrl+Shift+Enter to evaluate the function as an array formula.

- **Text and Logical Values**:
    - The function ignores non-numeric values (e.g., text or logical values) in the dataset.
    ```excel
    =MODE.MULT(1, 2, "text", FALSE, 2, 3, 3)
    ```
  Result: `{2, 3}`.

- **Error Values**:
    - If an error exists in the dataset, the function returns that error.

### Applications:

- **Statistical Analysis**: Identify the most common values in a dataset.
- **Market Research**: Analyze customer preferences or most frequently sold items.
- **Quality Control**: Detect common defects or issues in production lines.

> **Tip:** For datasets with a single mode, you can use `MODE.SNGL`. To return only the first mode in a multimodal
> dataset, `MODE.SNGL` can also be used.