<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ARABIC Function

The `ARABIC` function in Excel converts a Roman numeral (in text format) into its equivalent Arabic number (integer).
This is particularly useful for working with data containing Roman numerals and needing to process or analyze them
numerically.

### Syntax:

    ARABIC(text)

- **text**: This is a required argument. It is the Roman numeral, entered as text, that you want to convert to an Arabic
  number. The input is case-insensitive and can accept Roman numerals in the standard or less common formats.

### Examples:

1. `=ARABIC("X")` would return 10, as "X" represents the number 10 in Roman numerals.
2. `=ARABIC("IV")` would return 4, as "IV" represents the number 4 in Roman numerals.
3. `=ARABIC("MMXXIII")` would return 2023, as "MMXXIII" represents the year 2023 in Roman numerals.
4. `=ARABIC(A1)` would convert the Roman numeral in cell A1 to its equivalent Arabic number.

> **Note**: The `ARABIC` function returns a `#VALUE!` error if the input is not a valid Roman numeral. It is also
flexible with modern variations of Roman numerals but strictly requires correctly formatted values.