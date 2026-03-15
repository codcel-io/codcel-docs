<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## Excel's CONCATENATE Function

The `CONCATENATE` function in Excel is used to join two or more text strings into one single string. This function is useful when you want to combine data from different cells or add additional text to existing cell values.

### Syntax:

    CONCATENATE(text1, [text2], ...)


- **text1**: The first text value or string that you want to concatenate.
- **text2** (optional): Additional text values or strings you wish to concatenate. You can specify up to 255 additional text arguments.

### Examples:

1. `=CONCATENATE("Hello", " ", "World!")` would return `Hello World!`.
2. `=CONCATENATE(A1, " ", B1)` would combine the values in cells A1 and B1, separated by a space.

> **Note**: Starting with Excel 2016, the `CONCATENATE` function is being replaced by the `TEXTJOIN` and `CONCAT` functions to provide more powerful and flexible text joining capabilities. Although `CONCATENATE` is still available for backward compatibility, it's recommended to use the newer functions in the latest versions of Excel.