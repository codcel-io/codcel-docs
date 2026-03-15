<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TRIMRANGE Function

The `TRIMRANGE` function in Excel is used to **remove empty rows and columns from the edges of an array or range**. It trims leading and trailing blank rows and columns, returning a more compact array without affecting internal data.

## Key Features of `TRIMRANGE`:

- Removes empty rows from the top and bottom of an array.
- Removes empty columns from the left and right of an array.
- Preserves all internal data, including embedded blank cells.
- Works seamlessly with other dynamic array functions.
- Useful for cleaning up data ranges before further processing.

## Syntax:

```plaintext
TRIMRANGE(array)
```

- **array**: The array or range from which to remove empty rows and columns at the edges.

## How `TRIMRANGE` Works:

1. The function examines the input array from all four edges (top, bottom, left, right).
2. It identifies rows that are entirely empty at the top and bottom of the array.
3. It identifies columns that are entirely empty at the left and right of the array.
4. These empty edge rows and columns are removed from the result.
5. All internal data, including any blank cells within the data region, is preserved.
6. If the entire array is empty, `TRIMRANGE` returns an empty result.

## Examples:

### 1. Basic Trimming of a Range with Empty Edges:

If A1:D6 contains data with the first row and last column empty:

```excel
=TRIMRANGE(A1:D6)
```

**Result:**
```
Returns the array with the empty first row and last column removed
```

### 2. Trim a Range with Empty Rows at Top and Bottom:

If A1:C5 has empty rows 1 and 5:

```excel
=TRIMRANGE(A1:C5)
```

**Result:**
```
Returns only rows 2-4 with all columns
```

### 3. Trim a Range with Empty Columns on Both Sides:

If A1:E3 has empty columns A and E:

```excel
=TRIMRANGE(A1:E3)
```

**Result:**
```
Returns columns B:D with all rows
```

### 4. Combine with HSTACK to Clean Up Combined Arrays:

```excel
=TRIMRANGE(HSTACK(A1:B3, D1:E3))
```

**Result:**
```
Horizontally stacks two ranges and removes any empty edge rows or columns
```

### 5. Combine with VSTACK for Vertical Stacking:

```excel
=TRIMRANGE(VSTACK(A1:C2, A5:C6))
```

**Result:**
```
Vertically stacks ranges and trims any empty edges from the result
```

### 6. Clean Up Results from EXPAND:

```excel
=TRIMRANGE(EXPAND(A1:B2, 5, 5, ""))
```

**Result:**
```
Expands the array with empty strings, then trims back to original size
```

### 7. Use with IF to Conditionally Include Data:

```excel
=TRIMRANGE(IF(A1:D4<>"", A1:D4, ""))
```

**Result:**
```
Filters out empty cells and trims the resulting empty edges
```

### 8. Trim a Literal Array:

```excel
=TRIMRANGE({""," "," ";"A","B","C";""," "," "})
```

**Result:**
```
A   B   C
```
(Rows with only empty strings are trimmed)

## Notes:

- `TRIMRANGE` is available in Excel 365 and Excel 2021 or later versions.
- The function only removes completely empty rows and columns at the edges; internal blanks are preserved.
- Cells containing spaces or formulas returning empty strings ("") are considered empty for trimming purposes.
- `TRIMRANGE` is particularly useful after operations like `FILTER`, `EXPAND`, or `IF` that may create sparse arrays.
- The function does not modify the original data; it creates a new trimmed array.

## Applications:

- **Data Cleanup**: Remove extraneous empty rows and columns before analysis or export.
- **Dynamic Reporting**: Ensure reports only include populated areas of data.
- **Array Optimization**: Reduce array size after combining or filtering operations.
- **Formula Chaining**: Clean up intermediate results in complex dynamic array formulas.
- **Data Import**: Process imported data that may have irregular empty edges.

## Related Functions:

- **EXPAND**: Increases array dimensions by adding rows and/or columns with padding.
- **TAKE**: Extracts a specified number of rows or columns from an array.
- **DROP**: Excludes a specified number of rows or columns from an array.
- **HSTACK**: Horizontally combines arrays side by side.
- **VSTACK**: Vertically stacks arrays on top of each other.
- **FILTER**: Filters a range based on criteria, which may leave empty areas.
- **TOCOL**: Converts an array to a single column.
- **TOROW**: Converts an array to a single row.

> **Tip:** Use `TRIMRANGE` after combining multiple arrays with `HSTACK` or `VSTACK` to ensure the final result contains no unnecessary empty edges, especially when working with data of varying sizes.