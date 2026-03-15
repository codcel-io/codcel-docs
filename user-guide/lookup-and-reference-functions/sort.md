<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SORT

The `SORT` function in Excel is used to sort the contents of a range or array. The function can sort data in ascending
or descending order, based on one or more columns.

### Syntax

```excel
SORT(array, [sort_index], [sort_order], [by_col])
```

- **array**: The range or array to sort. This is the only required argument.
- **sort_index** (optional): A number indicating the row or column to sort by. If omitted, the `SORT` function will sort
  by the first column or row.
- **sort_order** (optional): A number specifying the sort order: 1 for ascending (default) or -1 for descending.
- **by_col** (optional): A logical value indicating the direction of the sort. `FALSE` (default) sorts by rows; `TRUE`
  sorts by columns.

### Examples

#### Example 1

Sort a list of numbers in ascending order:

```excel
=SORT(A1:A10)
```

#### Example 2

Sort a table based on the second column in descending order:

```excel
=SORT(A1:C10, 2, -1)
```

#### Example 3

Sort a range by columns rather than rows:

```excel
=SORT(A1:C10, 1, 1, TRUE)
```

### Sort by columns

#### Example Dataset 

Given the dataset in range `A1:C3`:

| A   | B   | C   |
|-----|-----|-----|
| 8   | 3   | 5   |
| 2   | 1   | 4   |
| 7   | 6   | 9   |

---

### Example 1: Sort Columns in Ascending Order

To sort columns based on the first row, in **ascending order**:

```excel
=SORT(A1:C3, 1, 1, TRUE)
```

**Result**:

| B   | C   | A   |
|-----|-----|-----|
| 3   | 5   | 8   |
| 1   | 4   | 2   |
| 6   | 9   | 7   |

**Explanation**:
- **`array`**: `A1:C3`
- **`sort_index`**: `1` (sort by the first row).
- **`sort_order`**: `1` (ascending order).
- **`by_col`**: `TRUE` (sort columns).

---

### Example 2: Sort Columns in Descending Order

To sort columns based on the second row, in **descending order**:

```excel
=SORT(A1:C3, 2, -1, TRUE)
```

**Result**:

| A   | C   | B   |
|-----|-----|-----|
| 8   | 5   | 3   |
| 2   | 4   | 1   |
| 7   | 9   | 6   |

**Explanation**:
- **`array`**: `A1:C3`
- **`sort_index`**: `2` (sort by the second row).
- **`sort_order`**: `-1` (descending order).
- **`by_col`**: `TRUE` (sort columns).

---

### Key Points
- **`by_col`** is essential for sorting columns:
  - If omitted or set to `FALSE`, sorting occurs row-wise.
  - If set to `TRUE`, sorting occurs column-wise. 
- Combine with functions like `FILTER` or `UNIQUE` for more advanced operations.

### Notes

- The `SORT` function is available in Excel for Microsoft 365 and Excel 2019.
- It does not alter the original data but returns a sortable array.
- Use `FILTER` or other functions for more complex sorting operations.