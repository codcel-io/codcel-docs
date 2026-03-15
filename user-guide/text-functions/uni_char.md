<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    UNICHAR(number)

- **number**: A Unicode number representing a specific character.

### Description:

The `UNICHAR` function in Excel returns the Unicode character that corresponds to the given numeric value. It is
typically used to input characters not easily accessible on a keyboard, such as special symbols, emojis, or characters
from different writing systems. The function is particularly useful when working with Unicode encodings or generating
specific text outputs.

### Examples:

1. `=UNICHAR(65)`  
   Result: `A`. Returns the Unicode character corresponding to the number `65`.

2. `=UNICHAR(9731)`  
   Result: ☃. Returns the snowman symbol, corresponding to its Unicode number.

3. `=UNICHAR(128516)`  
   Result: 😄. Provides the Unicode character for the smiling face emoji.

4. `=UNICHAR(8364)`  
   Result: €. Outputs the euro currency symbol.

### Notes:

- The `UNICHAR` function supports the full range of Unicode characters, so it can return letters, symbols, emojis, and
  characters from various languages.
- Use the `UNICODE` function in combination with `UNICHAR` to reverse the process, i.e., to get a Unicode number from a
  character.
- If the numeric value provided does not correspond to a valid Unicode character, the function will return a `#VALUE!`
  error.
- `UNICHAR` may not display certain extended Unicode characters properly if your system or font does not support them.