<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LEN Function

The `LEN` function in Excel returns the number of characters in a specified text string. It is helpful for counting characters, including spaces, punctuation, and numbers, within a cell or string of text.

### Syntax:

    LEN(text)

- **text**: The text string, cell reference, or text value whose length you want to determine.

### How It Works:

The `LEN` function counts every character in the specified text, including:
- Letters
- Numbers
- Spaces
- Special characters (e.g., punctuation marks)
- Any other visible characters

### Important Note:
The `LEN` function does **not** count formatting characters, such as those created by bolding, italics, or font color changes.

### Examples:

1. **Basic Usage with Text String**  
   `=LEN("Hello World")` would return `11`, as there are 11 characters, including the space.

2. **Counting Characters in a Cell**  
   If cell A1 contains the text `Excel 365`, then `=LEN(A1)` would return `9`, counting both the letters and the space.

3. **Using LEN with Other Functions**  
   You can combine `LEN` with other functions to perform more complex calculations. For example, to remove leading and trailing spaces from text before counting, you could use it with the `TRIM` function:  
   `=LEN(TRIM(A1))`.  
   This formula first removes extra spaces from the text in A1, then counts the remaining characters.

4. **Checking for Empty Cells**  
   Using `LEN` with an empty cell or a cell containing only spaces can reveal if a cell truly contains any characters.
    - `=LEN(A1)` returns `0` if cell A1 is empty.
    - If cell A1 has only spaces, `LEN(A1)` will return the count of those spaces.

> **Note**: The `LEN` function is a simple but effective way to measure text length in Excel, making it ideal for data validation, text processing, and more.