<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CONCAT Function

Introduced in Excel 2016, the `CONCAT` function is used to join multiple text strings into one single string. It's an improvement and simplification over the older `CONCATENATE` function, allowing you to combine text from a range of cells without having to reference each cell individually.

### Syntax:

    CONCAT(text1, [text2], ...)

- **text1, text2, ...**: The text values or ranges that you want to concatenate. This can include individual text strings, cell references, or cell ranges.

### Examples:

1. `=CONCAT("Hello", " ", "World!")` would return `Hello World!`.
2. `=CONCAT(A1, B1)` would combine the values in cells A1 and B1.
3. `=CONCAT(A1:A3)` would concatenate all values in the range A1 to A3.

> **Note**: One of the key advantages of `CONCAT` over `CONCATENATE` is its ability to handle ranges. Additionally, while `CONCATENATE` is still available in Excel for backward compatibility, it's recommended to use `CONCAT` or `TEXTJOIN` (which offers delimiter options) in newer versions of Excel for a more versatile text combining experience.