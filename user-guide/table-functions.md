<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Table Functions

This contains the list of table functions that are currently supported by Codcel.

> **Note**: If an Excel table function does not appear in this list, it is because it is currently not supported in this version of Codcel.

## Filter Functions

### [`FILTER`](./table-functions/filter.md)
Filters a range of data based on criteria you define.
- **Example:** `=FILTER(A1:B10, B1:B10>50)`

## Lookup Functions

### [`HLOOKUP`](./table-functions/hlookup.md)
Searches for a value in the first row of a table and returns a value in the same column from another row.
- **Example:** `=HLOOKUP("Product", A1:D5, 2, FALSE)`

### [`INDEX`](./table-functions/index.md)
Returns the value of a cell within a specified range, based on row and column numbers.
- **Example:** `=INDEX(A1:C10, 2, 3)`

### [`LOOKUP`](./table-functions/lookup.md)
Looks up a value in a range and returns a corresponding value from another range.
- **Example:** `=LOOKUP(40, A1:A10, B1:B10)`

### [`MATCH`](./table-functions/match.md)
Returns the relative position of a value in a range.
- **Example:** `=MATCH(50, A1:A10, 0)`

### [`VLOOKUP`](./table-functions/vlookup.md)
Searches for a value in the first column of a table and returns a value in the same row from another column.
- **Example:** `=VLOOKUP(101, A1:D10, 2, FALSE)`

### [`XLOOKUP`](./table-functions/xlookup.md)
Searches a range or array and returns an item corresponding to the first match it finds.
- **Example:** `=XLOOKUP(40, A1:A10, B1:B10)`

### [`XMATCH`](./table-functions/xmatch.md)
Returns the relative position of an item in an array, similar to `MATCH`, but with more flexibility.
- **Example:** `=XMATCH(50, A1:A10, 0, 1)`