<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    MID(text, start_num, num_chars)

- **text**: The text string from which you want to extract characters.
- **start_num**: The position of the first character you want to extract. The first character in `text` is 1.
- **num_chars**: The number of characters you want to extract from the `text`, starting at `start_num`.

### Description:

The `MID` function in Excel is used to extract a specific number of characters from a text string, starting at a
specified position. This function is particularly helpful when you need to extract substrings from within a longer text
string.

Its flexible parameters allow selection of any subset of the string based on your requirements.

For example:

    MID("text", start_num, num_chars) = extracted substring

### Examples:

1. `=MID("HelloWorld", 1, 5)` would return `"Hello"`, extracting the first 5 characters from "HelloWorld".
2. `=MID("DataProcessing", 5, 4)` would return `"Proc"`, which starts at the 5th character and extracts 4 characters.
3. `=MID("ExcelFunctions", 7, 9)` would return `"Functions"`, as it starts at the 7th character and continues for 9
   characters.
4. `=MID("123456789", 4, 3)` would return `"456"`, starting at the 4th character and extracting 3 characters.

### Notes:

- If `start_num` is greater than the current length of `text`, the `MID` function will return an empty string (`""`).
- If `start_num` is less than 1, Excel will return an error (`#VALUE!`).
- If `num_chars` is 0, an empty string (`""`) is returned.
- If `start_num + num_chars - 1` exceeds the length of `text`, the function will return all characters from `start_num`
  to the end of the `text`.
- Use the `MID` function when needing to extract substrings dynamically, especially for parsing or cleaning up text
  data.