<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    JIS(text)

- **text**: The text string containing half-width (single-byte) characters that you want to convert to full-width (double-byte) characters.

### Description:

The `JIS` function in Excel converts half-width (single-byte) characters in a text string to full-width (double-byte)
characters. This function is named after the Japanese Industrial Standard (JIS) character encoding and is primarily
designed for use with languages that support double-byte character sets (DBCS), such as Japanese, Chinese, and Korean.
In DBCS languages, characters can be represented as either full-width (taking up more space) or half-width.
For example, half-width characters like `ABC` will be converted to their full-width counterparts `ＡＢＣ`.

The `JIS` function is functionally equivalent to the `DBCS` function in Excel. Both perform the same half-width to
full-width conversion, and the `JIS` function is the inverse of the `ASC` function.

### Examples:

1. `=JIS("Hello")`
    - Returns: `Ｈｅｌｌｏ`
      (The half-width characters `Hello` are converted to full-width.)
2. `=JIS("12345")`
    - Returns: `１２３４５`
      (The half-width numbers `12345` are converted to full-width.)
3. `=JIS("!#$%")`
    - Returns: `！＃＄％`
      (Half-width punctuation is converted to its full-width equivalents.)

### Notes:

- The `JIS` function does not affect full-width characters; they remain unchanged.
- This function works specifically with DBCS languages, and its effects might not be apparent in locales that primarily
  use single-byte character sets.
- The `JIS` function is useful when formatting text for systems or applications that require full-width characters,
  such as certain East Asian typesetting and display contexts.
- If no half-width characters exist in the input string, the original text is returned unchanged.
- For converting full-width characters to their half-width (single-byte) versions, you can use the `ASC` function.
- The `JIS` function is equivalent to the `DBCS` function in Excel. Both perform the same conversion.