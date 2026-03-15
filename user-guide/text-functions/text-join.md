<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TEXTJOIN Function

Introduced in Excel 2016, the `TEXTJOIN` function allows users to concatenate (or join) multiple text strings from a range of cells using a specified delimiter. It offers more flexibility than both the older `CONCATENATE` and the newer `CONCAT` functions due to its ability to handle delimiters and ignore empty cells.

### Syntax:

    TEXTJOIN(delimiter, ignore_empty, text1, [text2], ...)


- **delimiter**: The character or characters you want to use as a separator between each text value.
- **ignore_empty**: A logical value (TRUE or FALSE). If TRUE, the function will skip any empty cells; if FALSE, it will include empty cells in the result.
- **text1, text2, ...**: The text values or ranges that you want to concatenate. This can include individual text strings, cell references, or cell ranges.

### Examples:

1. `=TEXTJOIN("-", TRUE, "2023", "10", "12")` would return `2023-10-12`.
2. Given cells A1:A3 containing values "Apple", "Banana", and "Cherry", respectively, `=TEXTJOIN(", ", TRUE, A1:A3)` would return `Apple, Banana, Cherry`.
3. Using the same range A1:A3, if A2 was empty and you used `=TEXTJOIN(", ", FALSE, A1:A3)`, the result would be `Apple, , Cherry`. If `ignore_empty` was set to TRUE, the result would be `Apple, Cherry`.

> **Note**: `TEXTJOIN` provides a more sophisticated way to combine text in Excel, especially when working with data that might have empty cells or when a delimiter is necessary.