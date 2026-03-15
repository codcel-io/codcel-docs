<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SEQUENCE Function

Introduced in Excel for Microsoft 365 and Excel 2019, the `SEQUENCE` function generates a list or array of sequential numbers. It's useful for creating a series of numbers in an array formula, without manually entering them.

### Syntax:

    SEQUENCE(rows, [columns], [start], [step])


- **rows**: The number of rows to fill with sequential numbers.
- **columns** (optional): The number of columns to fill with sequential numbers. If omitted, defaults to 1.
- **start** (optional): The first number in the sequence. If omitted, defaults to 1.
- **step** (optional): The increment for each subsequent number in the sequence. If omitted, defaults to 1.

### Examples:

1. `=SEQUENCE(4)` would generate an array with four rows filled with the numbers 1 to 4.
2. `=SEQUENCE(3, 2)` would create a 3x2 array: {{1, 2}, {3, 4}, {5, 6}}.
3. `=SEQUENCE(5, 1, 10, 2)` would produce a column of five numbers, starting from 10 and incrementing by 2: {10, 12, 14, 16, 18}.

### Usage Notes:
- The `SEQUENCE` function is particularly useful in scenarios where you need to create a series of dates, times, or even for use in custom data validation rules.
- One of the key advantages of `SEQUENCE` is its ability to generate dynamic arrays that automatically spill into adjacent cells, which means the function adjusts the output range based on the specified row and column counts.

> **Note**: The `SEQUENCE` function is only available in Excel for Microsoft 365 and Excel 2019 onwards. In earlier versions of Excel, similar results can be achieved with functions like `ROW`, `COLUMN`, and array formulas.