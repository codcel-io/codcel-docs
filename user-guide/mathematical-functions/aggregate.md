<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## AGGREGATE Function

The `AGGREGATE` function in Excel is a versatile function used to perform various mathematical and statistical
operations, such as summing, averaging, counting, or finding the maximum/minimum, while optionally ignoring hidden rows,
errors, or other data exclusions.

### Syntax:

    AGGREGATE(function_num, options, ref1, [ref2], ...)

- **function_num**: This is a required argument that specifies the operation to be performed (e.g., 1 for AVERAGE, 2 for
  COUNT, etc.). Each function number corresponds to a specific type of aggregation.
- **options**: This argument determines how the function should handle hidden rows, errors, or nested
  subtotals/aggregations. Use numeric values (0–7) to specify the desired options.
- **ref1, ref2, ...**: These are the ranges or arrays of data on which the aggregation function operates. The `ref2` and
  subsequent arguments are optional and depend on the selected aggregation function.

### Key Options:

1. **0** – Ignore all hidden rows, errors, nested subtotals, and aggregations.
2. **1** – Ignore hidden rows only.
3. **2** – Ignore errors only.
4. **3** – Ignore hidden rows and errors.
5. Other options up to **7** allow further customization for different use cases.

### Examples:

1. `=AGGREGATE(1, 3, A1:A10)`  
   This calculates the average (function number 1) of the range `A1:A10`, while ignoring all hidden rows and errors.

2. `=AGGREGATE(9, 1, B1:B20)`  
   This calculates the sum (function number 9) of the range `B1:B20`, while ignoring hidden rows only.

3. `=AGGREGATE(4, 2, C1:C15)`  
   This finds the maximum value of the range `C1:C15`, while ignoring errors.

### Supported Function Numbers:

Below is a list of the supported aggregation types and their corresponding `function_num` values:

| Function Number | Aggregation      |
|------------------|------------------|
| 1                | AVERAGE          |
| 2                | COUNT            |
| 3                | COUNTA           |
| 4                | MAX              |
| 5                | MIN              |
| 6                | PRODUCT          |
| 7                | STDEV.S          |
| 8                | STDEV.P          |
| 9                | SUM              |
| 10               | VAR.S            |
| 11               | VAR.P            |
| 12–19            | Additional functions for large/small data operations. |

### Notes:

- The `AGGREGATE` function is particularly useful for datasets that might contain errors or hidden rows, making it a
  better alternative to functions like `SUM` or `AVERAGE`.
- If a specified option is incompatible with the aggregation type, Excel may return a `#VALUE!` error.

> **Tip**: Experiment with different combinations of `function_num` and `options` to handle your specific data analysis
needs effectively.