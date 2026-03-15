<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    ASC(text)

- **text**: The text string from which you want to remove double-byte (full-width) characters.

### Description:

The `ASC` function in Excel is used to convert full-width (double-byte) characters in a text string to half-width (
single-byte) characters. This function is primarily designed for use with languages that support double-byte character
sets (DBCS), such as Japanese, Chinese, and Korean. In DBCS languages, characters can be represented as either
full-width (taking up more space) or half-width.
For example, full-width characters like `ＡＢＣ` will be converted to their single-byte counterparts `ABC`.

### Examples:

1. `=ASC("Ｈｅｌｌｏ")`
    - Returns: `Hello`  
      (`Ｈｅｌｌｏ` is a string with full-width characters.)
2. `=ASC("１２３４５")`
    - Returns: `12345`  
      (The full-width numbers `１２３４５` are converted to half-width.)
3. `=ASC("！＃＄％")`
    - Returns: `!#$%`  
      (Full-width punctuation is converted to its single-byte equivalents.)

### Notes:

- The `ASC` function does not affect half-width characters; they remain unchanged.
- This function works specifically with DBCS languages, and its effects might not be apparent in locales that primarily
  use single-byte character sets.
- The `ASC` function is useful when cleaning up text meant for systems or applications that only support single-byte
  characters.
- If no double-byte characters exist in the input string, the original text is returned unchanged.
- For converting single-byte characters to their full-width versions, you can use the `JIS` function in Excel.