<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MATCH Function

The `MATCH` function in Excel searches for a specified value in a range and returns the relative position of that item within the range. It's commonly used to locate the position of a specific value in a row, column, or table.

### Syntax:

    MATCH(lookup_value, lookup_array, [match_type])

- **lookup_value**: The value that you want to search for.
- **lookup_array**: The range of cells containing possible matches. This range can be a row, a column, or a one-dimensional array.
- **match_type** (optional):
    - `1` or omitted: `MATCH` finds the largest value less than or equal to `lookup_value`. `lookup_array` must be sorted in ascending order.
    - `0`: `MATCH` finds the first value exactly equal to `lookup_value`. `lookup_array` does not need to be sorted.
    - `-1`: `MATCH` finds the smallest value greater than or equal to `lookup_value`. `lookup_array` must be sorted in descending order.

### Examples:

1. `=MATCH(9, A1:A10, 0)` would search for the value `9` in the range `A1:A10` and return its relative position if it finds an exact match.
2. `=MATCH("Apple", B1:B5, 0)` would search for the text "Apple" in the range `B1:B5` and return the position of "Apple" within that range.
3. `=MATCH(15, C1:C10, 1)` assuming `C1:C10` is sorted in ascending order, would find the largest value less than or equal to 15.

#### Examples using Excel arrays:

4. `=MATCH(3, {1,2,3,4,5}, 0)` searches for `3` in the horizontal array `{1,2,3,4,5}` and returns `3` because `3` is the third element.
5. `=MATCH("B", {"A";"B";"C"}, 0)` searches for `"B"` in the vertical array `{"A";"B";"C"}` and returns `2` because `"B"` is the second element.
6. `=MATCH(2.5, {1,2,3,4}, 1)` returns `2`, because `2` is the largest value less than or equal to `2.5` in the array.

> **Note**: When using arrays: {1,2,3,4} instead of cell ranges: C1:C10 no tables are created. 
> arrays will allow MATCH to run in WASM

### Usage Notes:
- `MATCH` is frequently used with the `INDEX` function to retrieve a value at a found position.
- The function is case-insensitive, meaning it does not distinguish between uppercase and lowercase when matching text.
- If `MATCH` does not find a value, it returns the `#N/A` error.

> **Note**: Choosing the correct `match_type` is crucial for getting the expected results.

> **Note**: When match type is 1 or -1, Codcel will automatically order the lookup_array correctly.  This may give different results to Excel, if the lookup_array is not ordered correctly in Excel.

> **Note**: The lookup_array must not contain functions, if it does the match may not work correctly.