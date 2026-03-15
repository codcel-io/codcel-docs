<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VLOOKUP Function

The `VLOOKUP` function in Excel is used to search for a value in the first column of a table range and return a value in the same row from a specified column. The "V" in `VLOOKUP` stands for "Vertical".

### Syntax:

    VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])

- **lookup_value**: The value to search for in the first column of the table_array.
- **table_array**: The range of cells that contains the data to be searched.
- **col_index_num**: The column index number from which the corresponding value should be returned. For example, if you specify 2, the function will return the value from the second column of table_array.
- **[range_lookup]**: This is an optional argument.
    - If TRUE (or omitted), `VLOOKUP` will look for the closest match to the `lookup_value`. This assumes the first column in your table_array is sorted in ascending order.
    - If FALSE, `VLOOKUP` will look for an exact match. If there are multiple values that match the `lookup_value`, the first one found will be returned.

### Examples:

1. `=VLOOKUP(100, A2:B10, 2, FALSE)` would search for the value 100 in column A of the range A2:A10. If found, it would return the corresponding value from column B.
2. `=VLOOKUP("John", A2:C10, 3, TRUE)` might search for the name "John" in column A of the range A2:A10 and return the corresponding value from column C. If the exact name isn't found, it will return the nearest match if the data is sorted.
3. `=VLOOKUP("Apple", {"Apple",5;"Banana",3;"Cherry",8}, 2, FALSE)` would search for "Apple" in the first column of the array and return 5 from the second column. This example uses a literal array where the data is defined directly in the formula using curly braces, with semicolons separating rows and commas separating columns.

> **Note**: Where an array is used: {"Apple",5;"Banana",3;"Cherry",8} then this does not create a table, but instead is put in memory. This is compatible with WASM.

It's important to note that `VLOOKUP` is case-insensitive and will only search for values in the first column of the specified table_array.

> **Note**: When range_lookup is TRUE, Codcel will automatically order the first column in your table_array in ascending order.  This may give different results to Excel, if the table is not ordered correctly in Excel.

> **Note**: The first column must not contain functions, if it does the search may not work correctly.