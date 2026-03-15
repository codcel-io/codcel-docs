<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## HLOOKUP Function

The `HLOOKUP` function in Excel is used for horizontal lookup. It searches for a specified value in the top row of a table or range and returns a value in the same column from a specified row.

### Syntax:

   HLOOKUP(lookup_value, table_array, row_index_num, [range_lookup])


- **lookup_value**: The value to search for in the first row of the table or range.
- **table_array**: The range of cells containing the data to be searched.
- **row_index_num**: The row number in `table_array` from which to retrieve the value. For example, `2` would return a value from the second row of `table_array`.
- **range_lookup** (optional): A logical value that specifies whether to look for an exact match or an approximate match.
   - If `TRUE` or omitted, `HLOOKUP` will look for the nearest match to `lookup_value`. This requires the first row of `table_array` to be in ascending order.
   - If `FALSE`, `HLOOKUP` will look for an exact match. If multiple values match, the first one found is used.

### Examples:

1. `=HLOOKUP("Apple", A1:D2, 2, FALSE)` would search for "Apple" in the first row of `A1:D2`. If found, it returns the value from the second row in the same column.
2. `=HLOOKUP(3, E1:H4, 4, TRUE)` might search for the value `3` in the first row of `E1:H4` and return the corresponding value from the fourth row. If the exact value is not found, it will return the nearest match.
3. `=HLOOKUP("Quarter 1", {"Quarter 1","Quarter 2","Quarter 3","Quarter 4";100,150,200,175}, 2, FALSE)` would search for "Quarter 1" in the array and return `100` from the second row.

> **Note**: Where an array is used: {"Quarter 1","Quarter 2","Quarter 3","Quarter 4";100,150,200,175} then this does not create a table, but instead is put in memory. This is compatible with WASM.


### Usage Notes:
- `HLOOKUP` is useful for data organized horizontally, where the lookup value is in a row at the top of the data set.
- It's important to ensure that the data in the first row is sorted when using approximate match (`TRUE` or omitted for `range_lookup`).

> **Note**: `HLOOKUP` is less commonly used than `VLOOKUP`, which performs a vertical search. For more complex lookups, or when dealing with unsorted data, consider using the `INDEX` and `MATCH` functions together, or the newer `XLOOKUP` function in Excel 365 and Excel 2019.

> **Note**: When range_lookup is TRUE, Codcel will automatically order the first row in your table_array in ascending order.  This may give different results to Excel, if the table is not ordered correctly in Excel.

> **Note**: The first row must not contain functions, if it does the search may not work correctly.