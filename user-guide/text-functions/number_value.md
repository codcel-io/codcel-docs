<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    NUMBERVALUE(text, [decimal_separator], [group_separator])

- **text**: The text value that you want to convert into a number.
- **decimal_separator** (optional): The character used as the decimal separator in the `text`. If omitted, your system's
  default decimal separator will be used.
- **group_separator** (optional): The character used as the grouping separator (e.g., thousands separator) in the
  `text`. If omitted, your system's default grouping separator will be used.

### Description:

The `NUMBERVALUE` function in Excel converts a text representation of a number into an actual numeric value. This
function is particularly useful when working with text data from external sources or systems that use different decimal
or grouping separators.

This function ensures accurate conversion by specifying custom separators, which can handle regional or international
differences in number formatting.

For example:

    NUMBERVALUE("text", [decimal_separator], [group_separator]) = numeric value

### Examples:

1. `=NUMBERVALUE("1,234.56")` would return `1234.56` based on the default system separators.
2. `=NUMBERVALUE("1.234,56", ",", ".")` would return `1234.56`, where `,` is defined as the decimal separator and `.` as
   the group separator.
3. `=NUMBERVALUE("12345", ".", ",")` would return `12345`, as no grouping or decimal is used in the text.
4. `=NUMBERVALUE("7 500", ".", " ")` would return `7500`, with a space as the grouping separator.

### Notes:

- The `NUMBERVALUE` function is locale-independent and works even when the separators in the text differ from the
  system's default settings.
- If the `text` argument contains an invalid numeric format, the function will return a `#VALUE!` error.
- Leading or trailing spaces in the `text` are ignored.
- This function is especially helpful for handling data imported from external systems or regions with varying number
  formatting practices.