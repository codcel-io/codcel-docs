<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## XLOOKUP Function  
Introduced in Excel for Microsoft 365 and Excel 2019, `XLOOKUP` is a powerful function that searches a range or an array, and returns an item corresponding to the first match it finds. It is a more versatile and flexible successor to the older `VLOOKUP` and `HLOOKUP` functions, allowing for horizontal and vertical lookups, as well as lookups to the left of the key values.

### Syntax:

   XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found], [match_mode], [search_mode])


- **lookup_value**: The value to search for.
- **lookup_array**: The array or range to search.
- **return_array**: The array or range from which to return a value.
- **if_not_found** (optional): The value to return if `lookup_value` is not found. If omitted, `#N/A` is returned.
- **match_mode** (optional): Specifies the match type:
   - `0` for an exact match (default).
   - `-1` for an exact match, or the next smaller item if not found.
   - `1` for an exact match, or the next larger item if not found.
   - `2` for a wildcard match.
- **search_mode** (optional): Specifies the search mode:
   - `1` for a search that starts at the first item (default).
   - `-1` for a reverse search starting at the last item.
   - `2` for a binary search (only for sorted data) that starts at the first item.
   - `-2` for a binary search (only for sorted data) that starts at the last item.

### Examples:

1. `=XLOOKUP("Apple", A2:A5, B2:B5)` would search for "Apple" in the range `A2:A5` and return the corresponding value from the range `B2:B5`.
2. `=XLOOKUP(100, D1:D10, A1:A10, "Not found")` would search for the value `100` in `D1:D10` and return the corresponding value from `A1:A10`. If `100` is not found, it returns "Not found".
3. `=XLOOKUP("*berry", FruitsColumn, PricesColumn, ,2)` uses wildcard matching to find any fruit ending in "berry" and return its price.
4. `=XLOOKUP("Banana", {"Apple";"Banana";"Cherry"}, {"Red";"Yellow";"Red"})` would search for "Banana" in the array `{"Apple";"Banana";"Cherry"}` and return the corresponding value "Yellow" from the array `{"Red";"Yellow";"Red"}`.

> **Note**: Where an array is used in both arrays: {"Apple";"Banana";"Cherry"} and {"Red";"Yellow";"Red"} then this does not create a table, but instead is put in memory. This is compatible with WASM.

### Usage Notes:
- `XLOOKUP` can replace both `VLOOKUP` and `HLOOKUP` and offers additional functionalities like searching in any direction and returning a default value if no match is found.
- It simplifies many lookup scenarios and reduces the need for complex combinations of `INDEX` and `MATCH`.

> **Note**: `XLOOKUP` is available in Excel for Microsoft 365 and Excel 2019 onwards. It's not available in earlier versions of Excel.

> **Note**: The lookup_array must not contain functions.  If it does the lookup will not work correctly.