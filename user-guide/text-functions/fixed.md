<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

FIXED(number, [decimals], [no_commas])

- **number**: The number to be formatted.
- **decimals** *(optional)*: The number of digits to display to the right of the decimal point. Defaults to 2 if
  omitted.
- **no_commas** *(optional)*: A Boolean value where `TRUE` omits commas in the resulting text, and `FALSE` includes
  them. Defaults to `FALSE` if omitted.

### Description:

The `FIXED` function in Excel is used to round a number to a specified number of decimal places and format it as text.
It provides the option to include or exclude thousands separators (commas).

This function is useful when creating reports or displaying values that need consistent accounting or currency
formatting.

For example:
FIXED(number) = "###,###.##" (formatted as text)

### Examples:

1. `=FIXED(1234.567, 2)` would return `"1,234.57"`, rounding to two decimal places and including commas.
2. `=FIXED(1234.567, 0)` would return `"1,235"`, rounding to the nearest whole number.
3. `=FIXED(1234.567, 3, TRUE)` would return `"1234.567"`, formatted to three decimal places without commas.
4. `=FIXED(-9876.543, 1)` would return `"-9,876.5"`, rounding to one decimal place and including commas.
5. `=FIXED(1000, 0, TRUE)` would return `"1000"`, with no decimals or commas.

### Notes:

- The `FIXED` function always returns its result as text, even though the input is numeric.
- If the `decimals` argument is negative, the function rounds the number to the left of the decimal point. For example,
  `=FIXED(1234.567, -1)` would return `"1,230"`.
- When the `no_commas` argument is set to `TRUE`, thousands separators are omitted.
- The function is particularly useful for presenting data in a user-friendly and formatted way.
- Formatting applied by `FIXED` is purely cosmetic (as text) and does not affect the underlying numeric value used in
  calculations. For calculations, you should use other rounding functions like `ROUND`, `ROUNDUP`, or `ROUNDDOWN`.