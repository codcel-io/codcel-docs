<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SUBTOTAL Function

The `SUBTOTAL` function in Excel returns a **subtotal value** for a given range of data. It is particularly useful for
calculating data summaries (e.g., averages, sums, counts) across filtered or visible rows, depending on the specified
calculation type.

### Key Features of SUBTOTAL:

- Supports multiple aggregation types such as `SUM`, `AVERAGE`, `COUNT`, `MAX`, `MIN`, etc.
- Can optionally exclude rows that are hidden or filtered out, making it ideal for working with dynamic datasets.
- Versatile function that adapts to changes in data visibility, making it better suited than standard aggregation
  functions in specific scenarios.

### Syntax:

```plaintext
SUBTOTAL(function_num, range1, [range2], ...)
```

- **function_num**: A number that specifies the type of calculation to perform. The function number also determines
  whether the hidden rows are included or ignored:
    - Numbers `1–11`: Includes both hidden and visible rows.
    - Numbers `101–111`: Excludes manually hidden rows and considers only visible rows.
- **range1**: The first data range for the calculation.
- **[range2], ...** (optional): Additional ranges to include in the calculation.

### Function Numbers and Their Operations:

| Function Number | Operation  | Includes Hidden Rows | Ignores Hidden Rows |
|------------------|------------|----------------------|----------------------|
| `1` / `101`     | AVERAGE    | ✓ (1)               | ✓ (101)             |
| `2` / `102`     | COUNT      | ✓ (2)               | ✓ (102)             |
| `3` / `103`     | COUNTA     | ✓ (3)               | ✓ (103)             |
| `4` / `104`     | MAX        | ✓ (4)               | ✓ (104)             |
| `5` / `105`     | MIN        | ✓ (5)               | ✓ (105)             |
| `6` / `106`     | PRODUCT    | ✓ (6)               | ✓ (106)             |
| `7` / `107`     | STDEV      | ✓ (7)               | ✓ (107)             |
| `8` / `108`     | STDEVP     | ✓ (8)               | ✓ (108)             |
| `9` / `109`     | SUM        | ✓ (9)               | ✓ (109)             |
| `10` / `110`    | VAR        | ✓ (10)              | ✓ (110)             |
| `11` / `111`    | VARP       | ✓ (11)              | ✓ (111)             |

### Examples:

1. `=SUBTOTAL(9, A1:A10)`  
   Calculates the sum (`function_num = 9`) of all values in the range `A1:A10`, including hidden rows.  
   **Result**: Total of all values, hidden or visible.

2. `=SUBTOTAL(109, A1:A10)`  
   Calculates the sum (`function_num = 109`) of all **visible values** in the range `A1:A10`. Hidden rows are ignored.  
   **Result**: Total of visible rows only.

3. `=SUBTOTAL(103, B1:B15)`  
   Counts the number of non-empty cells (visible only) in the range `B1:B15`.  
   **Result**: Count of non-empty visible rows.

4. `=SUBTOTAL(101, C1:C5)`  
   Computes the average of the visible values only in the range `C1:C5`.  
   **Result**: Average of visible values.

### Notes:

- The `SUBTOTAL` function adapts dynamically to filters applied in Excel tables or ranges.
- Manually hidden rows (using `Hide Row`) will not be included when using function numbers `101–111`.
- The function is superior to basic functions like `SUM` or `AVERAGE` when managing filtered datasets as it ensures
  accurate calculations reflecting the data's visibility.

> There is currently no implementation of HIDDEN ROWS in Codcel.

> **Tip**: Use `SUBTOTAL` for flexible aggregation functions in dynamic datasets, especially when working with filters
or hidden rows.

 