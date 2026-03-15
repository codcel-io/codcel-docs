<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    TEXTBEFORE(text, delimiter, [instance_num], [match_mode], [if_not_found])

- **text**: The text string you want to search within.
- **delimiter**: The text or character(s) before which you want to extract the text.
- **instance_num**: *(Optional)* Specifies which occurrence of the delimiter to use. Defaults to `1`. Negative numbers
  count from the end.
- **match_mode**: *(Optional)* Can be set to `0` (default) for case-sensitive matching or `1` for case-insensitive
  matching.
- **if_not_found**: *(Optional)* Specifies the value to return if the delimiter is not found. Defaults to a `#N/A`
  error.

### Description:

The `TEXTBEFORE` function in Excel extracts the portion of a text string that appears before a specified delimiter. It
is useful for scenarios like extracting usernames from email addresses, isolating labels before a special character, or
working with structured text data.

This versatile function simplifies text processing by enabling automated extraction of text segments based on specified
delimiters.

### Examples:

1. `=TEXTBEFORE("username@domain.com", "@")`  
   Result: Returns `"username"` (text before the `@` symbol).

2. `=TEXTBEFORE("1-2-3-4-5", "-", 3)`  
   Result: Returns `"1-2"`. (Stops at the third occurrence of the delimiter.)

3. `=TEXTBEFORE("fruit:apple|fruit:banana|fruit:cherry", "|", -1)`  
   Result: Returns `"fruit:banana"` (matches the text before the last occurrence of the delimiter).

4. `=TEXTBEFORE("HELLO|WORLD|EXCEL", "|", 2)`  
   Result: Returns `"HELLO"` (text before the second `|`).

5. `=TEXTBEFORE("data.split.example", ".", , , "Not Found")`  
   Result: Returns `"data.split"` (text before the first `.`). If no delimiter is found, it would return `"Not Found"`.

### Notes:

- Negative values for **instance_num** allow working backward from the end of the string to find text before a previous
  delimiter occurrence.
- Use the **if_not_found** parameter to provide custom fallback values for cases where the specified delimiter doesn't
  exist in the string.
- The **match_mode** parameter is particularly helpful when dealing with case-sensitive or case-insensitive scenarios.
- Combining `TEXTBEFORE` with other text functions, like `TEXTAFTER` or `TEXTSPLIT`, can achieve more complex text
  parsing and manipulation tasks.