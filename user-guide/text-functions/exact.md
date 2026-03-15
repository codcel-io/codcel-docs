<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

EXACT(text1, text2)

- **text1**: The first text string to be compared.
- **text2**: The second text string to be compared.

### Description:

The `EXACT` function in Excel is used to compare two text strings to determine if they are exactly the same. The
function is **case-sensitive** and checks for both character matches and capitalization.

It is particularly useful when you want to validate data and ensure uniformity, especially when managing case-sensitive
data such as passwords or IDs.

For example:

EXACT(text1, text2) = TRUE or FALSE

### Examples:

1. `=EXACT("Hello", "Hello")` would return `TRUE`, because the text strings are identical in both content and case.
2. `=EXACT("Data", "data")` would return `FALSE`, because the function is case-sensitive, and "D" is not the same as "
   d".
3. `=EXACT("123", "123 ")` would return `FALSE`, because the second text string contains an additional space character.
4. `=EXACT("Excel", "excel")` would return `FALSE`, because "E" (uppercase) is not the same as "e" (lowercase).
5. `=EXACT("TEXT", "TEXT")` would return `TRUE`, since both strings are identical and in the same case.

### Notes:

- The `EXACT` function is case-sensitive, which means that "ABC" is not the same as "abc".
- It is often used to validate user inputs, match case-sensitive strings, or detect differences in data.
- If both text strings are exactly the same, the function returns `TRUE`. Otherwise, it returns `FALSE`.
- The function can compare text, numbers, and special characters, but it does not ignore extra spaces or hidden
  characters.
- If either of the arguments is empty, the result would be `FALSE` (e.g., `=EXACT("Text", "")`).