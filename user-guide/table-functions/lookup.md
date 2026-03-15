<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LOOKUP Function

The `LOOKUP` function in Excel is used to search for a value in a row or column range and returns a corresponding value from a different row or column.

### Syntax:

There are two forms of the `LOOKUP` function:

1. Vector form:

    LOOKUP(lookup_value, lookup_vector, [result_vector])

- **lookup_value**: The value you want to search for.
- **lookup_vector**: A range that contains only one row or one column. The values in this range should be sorted in ascending order.
- **result_vector** (optional): A range that contains only one row or one column. It must be the same size as `lookup_vector`.

2. Array form:

    LOOKUP(lookup_value, array)

- **lookup_value**: The value you want to search for.
- **array**: A range of cells containing text, numbers, or logical values.

### Examples:

1. Vector form: Assuming `A1:A4` contains `{1, 2, 3, 4}` and `B1:B4` contains `{"A", "B", "C", "D"}`, the formula `=LOOKUP(3, A1:A4, B1:B4)` would return `"C"`.
2. Array form: Given the same ranges, the formula `=LOOKUP(3, A1:B4)` would return `3` because `LOOKUP` in array form returns a value from the same row but the last column of the array.

> **Note**: Where an array is used: {"A", "B", "C", "D"} then this does not create a table, but instead is put in memory. This is compatible with WASM.

> **Note**: The `LOOKUP` function will return the largest value less than or equal to `lookup_value` if an exact match is not found. This is why it is important that `lookup_vector` is sorted in ascending order for the vector form. If `lookup_value` is smaller than the smallest value in `lookup_vector`, the `LOOKUP` function will return an error.