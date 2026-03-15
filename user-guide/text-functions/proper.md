<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    PROPER(text)

- **text**: The text string that you want to convert to proper case.

### Description:

The `PROPER` function in Excel capitalizes the first letter of each word in a given text string while converting the
remaining letters to lowercase. It is particularly useful for formatting text, such as names or titles, where proper
capitalization is required.

This function treats any character that is not a letter (such as spaces, punctuation marks, or numbers) as a word
separator.

For example:

    PROPER(text) = Properly Formatted Text

### Examples:

1. `=PROPER("hello world")` would return `Hello World`.
2. `=PROPER("JOHN DOE")` would return `John Doe`.
3. `=PROPER("123main STREET")` would return `123Main Street`.
4. `=PROPER("a b-c.d")` would return `A B-C.D`, treating non-letter characters as word separators.
5. `=PROPER("EXCEL proper FUNCTION")` would return `Excel Proper Function`.

### Notes:

- Words are considered to start after any non-letter character, including spaces, punctuation, or numbers.
- This function is case-insensitive for input but ensures the output is consistently formatted.
- It does not modify numbers or special characters within the string; only alphabetic characters are affected.
- It may not correctly handle certain scenarios where specific words (e.g., lowercase prepositions or acronyms) require
  non-standard capitalization.