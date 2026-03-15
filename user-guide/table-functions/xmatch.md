<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## XMATCH Function

The `XMATCH` function searches for a specified item in an array or range of cells, and then returns the relative position of that item. `XMATCH` provides more flexibility and functionality compared to the older `MATCH` function, including new search modes and the ability to search in reverse order.

### Syntax:

   XMATCH(lookup_value, lookup_array, [match_mode], [search_mode])



- **lookup_value**: The value to search for in the `lookup_array`.
- **lookup_array**: The array or range of cells that contains the possible values.
- **match_mode** (optional): Specifies the match type.
   - `0` or omitted: Exact match. If no exact match is found, returns `#N/A`.
   - `-1`: Exact match or next smaller item.
   - `1`: Exact match or next larger item.
   - `2`: A wildcard match where `?` matches any single character and `*` matches any sequence of characters.
- **search_mode** (optional): Specifies the search mode.
   - `1` or omitted: Search begins at the first item in the `lookup_array`.
   - `-1`: Search begins at the last item in the `lookup_array`.
   - `2`: Performs a binary search that requires the `lookup_array` to be sorted in ascending order. This mode is faster for large arrays.
   - `-2`: Performs a binary search that requires the `lookup_array` to be sorted in descending order.

### Examples:

1. `=XMATCH(5, A1:A10)` would search for the number `5` in the range `A1:A10` and return its relative position.
2. `=XMATCH("apple", B1:B5, 0, 1)` would look for the word "apple" in the range `B1:B5` for an exact match, starting from the first item.
3. `=XMATCH(100, C1:C20, -1, 1)` would search for the value `100` in the range `C1:C20`, returning the position of the nearest value that is smaller than or equal to `100` if an exact match is not found.
4. `=XMATCH("banana", {"apple";"banana";"cherry";"date"})` would search for "banana" in the Excel array constant and return `2` (its position in the array).

> **Note**: Where an array is used: {"apple";"banana";"cherry";"date"} then this does not create a table, but instead is put in memory. This is compatible with WASM.


### Usage Notes:
- `XMATCH` is a powerful tool for dynamic arrays,