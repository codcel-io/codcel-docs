<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    UPPER(text)

- **text**: A text string or cell reference containing the text that you want to convert to uppercase.

### Description:

The `UPPER` function in Excel converts all lowercase letters in a given text string to their uppercase equivalents.
Non-alphabetic characters, numbers, and uppercase letters remain unchanged.

### Examples:

1. `=UPPER("hello")`  
   Result: `HELLO`. Converts all lowercase letters in "hello" to uppercase.

2. `=UPPER("Excel123")`  
   Result: `EXCEL123`. Converts only the lowercase letters in "Excel123" to uppercase. Numbers remain unaffected.

3. `=UPPER("good Morning!")`  
   Result: `GOOD MORNING!`. Converts "good Morning!" to uppercase, leaving punctuation unchanged.

4. `=UPPER(A1)`  
   Result: If cell `A1` contains "dynamic text", the function returns `DYNAMIC TEXT`.

### Notes:

- The `UPPER` function is useful for standardizing text data to uppercase for better comparison or uniform display.
- This function does not change numbers, spaces, or special characters.
- If the `text` argument is empty, it will return an empty string `""`.