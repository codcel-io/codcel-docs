<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    LEFTB(text, [num_bytes])

- **text**: The text string from which you want to extract characters. This can be a direct string, a cell reference, or the result of another function.
- **num_bytes** (optional): The number of bytes to extract starting from the left side of the string. If omitted, it defaults to 1.

### Description:

The `LEFTB` function in Excel returns the first character or characters in a text string, based on the number of bytes
you specify rather than the number of characters. This distinction is important when working with double-byte character
set (DBCS) languages such as Japanese, Chinese, and Korean, where a single character can occupy two bytes. In single-byte
character set (SBCS) languages such as English, `LEFTB` behaves identically to the `LEFT` function because each
character is one byte.

### Examples:

1. `=LEFTB("Excel", 2)`
    - Returns: `"Ex"`
      (In an SBCS environment, the first 2 bytes correspond to the first 2 characters.)
2. `=LEFTB("Excel")`
    - Returns: `"E"`
      (When `num_bytes` is omitted, it defaults to 1, returning the first byte.)
3. `=LEFTB(A1, 4)`
    - Returns the first 4 bytes of text from cell A1.
      (In an SBCS environment, this is equivalent to `=LEFT(A1, 4)`.)
4. `=LEFTB("Excel", 10)`
    - Returns: `"Excel"`
      (If `num_bytes` exceeds the byte length of the text, the entire string is returned.)

### Notes:

- In SBCS languages (e.g., English), `LEFTB` returns the same results as `LEFT` because each character equals one
  byte. The difference only becomes apparent in DBCS languages where characters may occupy two bytes.
- If `num_bytes` is greater than the byte length of the text string, the `LEFTB` function will return the entire
  string without any error.
- If `num_bytes` is set to 0, the result will be an empty string (`""`).
- If `num_bytes` is negative, Excel will return a `#VALUE!` error.
- The `num_bytes` argument counts bytes, not characters. When working with DBCS text, be mindful that a double-byte
  character occupies positions for two bytes.
- For character-based extraction from the left (rather than byte-based), use the `LEFT` function.
- The `LEFTB` function is equivalent to `LEFT` in Excel when the default language setting is a single-byte character
  set language. In DBCS language environments, `LEFTB` counts each double-byte character as 2 bytes.