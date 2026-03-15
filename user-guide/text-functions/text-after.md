<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    TEXTAFTER(text, delimiter, [instance_num], [match_mode], [if_not_found])

- **text**: The text string you want to search within.
- **delimiter**: The text or character(s) after which you want to extract the text.
- **instance_num**: *(Optional)* Specifies which occurrence of the delimiter to use. Defaults to `1`. Negative numbers
  count from the end.
- **match_mode**: *(Optional)* Can be set to `0` (default) for case-sensitive matching or `1` for case-insensitive
  matching.
- **if_not_found**: *(Optional)* Specifies the value to return if the delimiter is not found. Defaults to a `#N/A`
  error.

### Description:

The `TEXTAFTER` function in Excel extracts the portion of a text string that appears after a specified delimiter. It is
useful for parsing structured data, such as extracting the domain name from an email address, fetching data after a
specific character, or parsing text with repeated patterns.

This function simplifies text manipulation by automating the process of finding text patterns and extracting relevant
components.

### Examples:

1. `=TEXTAFTER("example@domain.com", "@")`  
   Result: Returns `"domain.com"` (text after the `@` symbol).

2. `=TEXTAFTER("A,B,C,D,E", ",", 3)`  
   Result: Returns `"C,D,E"`. (Starts with the third occurrence of the delimiter.)

3. `=TEXTAFTER("ONE-two-three-FOUR", "-", -1)`  
   Result: Returns `"FOUR"` (matches the last occurrence of the delimiter).

4. `=TEXTAFTER("Hello|World|Excel", "|", 2)`  
   Result: Returns `"World|Excel"` (from the second `|` onward).

5. `=TEXTAFTER("example.data", "/", , , "Not Found")`  
   Result: Returns `"Not Found"` since the delimiter `/` was not found in the input string.

### Notes:

- Negative values for **instance_num** are useful for extracting text after the last, second-to-last, etc., appearance
  of the delimiter.
- Use the **if_not_found** parameter to handle cases where the specified delimiter does not exist in the string.
- Combining `TEXTAFTER` with other text functions (e.g., `TEXTBEFORE`, `TEXTSPLIT`) enables complex text parsing and
  manipulation.
- The **match_mode** parameter allows for precise control over case sensitivity in text pattern searches.