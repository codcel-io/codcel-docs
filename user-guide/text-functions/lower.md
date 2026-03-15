<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

LOWER(text)

- **text**: The text string that you want to convert to lowercase.

### Description:

The `LOWER` function in Excel is used to convert all uppercase letters in a text string to lowercase letters. Any
non-alphabetic characters, such as numbers, symbols, or spaces, are not affected by this function.

This function is useful when standardizing the case of text data, especially for consistency in data preprocessing or
comparison scenarios.

### Examples:

1. `=LOWER("HELLO WORLD")` would return `"hello world"`.
2. `=LOWER("Excel Function")` would return `"excel function"`.
3. `=LOWER("123 ABC!@#")` would return `"123 abc!@#"`.
4. `=LOWER("MiXeD CaSe")` would return `"mixed case"`.
5. `=LOWER(A1)` would return the lowercase version of the text in cell `A1`.

### Notes:

- The `LOWER` function only affects uppercase alphabetic characters. It does not modify numbers, spaces, or other
  symbols.
- If the `text` argument is a blank cell or an empty string, the function will return an empty string.
- This function is useful for cleaning or normalizing data before performing operations like comparisons or searches,
  where case sensitivity might create inconsistencies.