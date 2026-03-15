<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    CLEAN(text)

- **text**: The text string from which you want to remove non-printable characters.

### Description:

The `CLEAN` function in Excel is used to remove all non-printable characters from a given text string. Non-printable
characters are often used to represent control characters in text data, which may not be displayed or printed. These
characters can sometimes occur when importing data from other applications or systems.

The function is particularly useful for cleaning up data that contains hidden characters often causing issues during
data processing.

For example:

    CLEAN(text) = text without non-printable characters

### Examples:

1. `=CLEAN("Hello" & CHAR(7))` would return `"Hello"`, because `CHAR(7)` (a non-printable bell character) is removed.
2. `=CLEAN("Data" & CHAR(13) & "More Data")` would return `"DataMore Data"`, as `CHAR(13)` (a non-printable carriage
   return) is removed.
3. `=CLEAN("GoodCOPY" & CHAR(27))` would return `"GoodCOPY"`, since `CHAR(27)` (an escape character) is removed.
4. `=CLEAN("Welcome"&CHAR(10))` would return `"Welcome"`, because `CHAR(10)` (a line break) is stripped from the text.

### Notes:

- The `CLEAN` function is designed for removing the first 32 non-printable ASCII characters (codes 0 through 31).
- It does not remove all whitespace characters like spaces, tabs, or non-breaking spaces. For trimming spaces, use the
  `TRIM` function.
- If no non-printable characters are found in the input text, the function returns the original text unchanged.
- The `CLEAN` function is especially helpful for improving compatibility and formatting of data when working with data
  imported from systems, files, or web content.