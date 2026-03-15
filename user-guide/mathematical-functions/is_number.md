<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ISNUMBER Function

The `ISNUMBER` function in Excel checks whether a value is a number. It is useful for determining if a cell contains a
numeric value.

### Syntax:

    ISNUMBER(value)

- **value**: The value you want to test to see if it is a number.

### Examples:

1. `=ISNUMBER(123)` would return TRUE.
2. `=ISNUMBER("Excel")` would return FALSE.
3. `=ISNUMBER(A1)` would return TRUE if the cell A1 contains a number, otherwise FALSE.
4. `=ISNUMBER("123")` would return FALSE.

> **Note**: The `ISNUMBER` function is especially helpful when analyzing data sets to ensure that numeric operations are
only performed on numeric data.