<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    LENB(text)

- **text**: The text string whose length in bytes you want to determine. This can be a direct string, a cell reference, or the result of another function.

### Description:

The `LENB` function in Excel returns the number of bytes used in a text string rather than the number of characters. This
distinction is important when working with double-byte character set (DBCS) languages such as Japanese, Chinese, and
Korean, where a single character can occupy two bytes. In single-byte character set (SBCS) languages such as English,
`LENB` behaves identically to the `LEN` function because each character is one byte.

### Examples:

1. `=LENB("Hello")`
    - Returns: `5`
      (In an SBCS environment, each character is 1 byte, so "Hello" is 5 bytes.)
2. `=LENB("")`
    - Returns: `0`
      (An empty string contains 0 bytes.)
3. `=LENB(A1)`
    - Returns the byte length of the text in cell A1.
      (In an SBCS environment, this is equivalent to `=LEN(A1)`.)
4. `=LENB("Excel Functions")`
    - Returns: `15`
      (In an SBCS environment, each character including the space is 1 byte.)

### Notes:

- In SBCS languages (e.g., English), `LENB` returns the same results as `LEN` because each character equals one
  byte. The difference only becomes apparent in DBCS languages where characters may occupy two bytes.
- Spaces are counted as bytes. For example, `=LENB(" ")` returns `1` in an SBCS environment.
- `LENB` counts all characters in the text string, including leading and trailing spaces, punctuation, and numbers.
- If `text` is an empty string (`""`), `LENB` returns `0`.
- For character-based length measurement (rather than byte-based), use the `LEN` function.
- The `LENB` function is equivalent to `LEN` in Excel when the default language setting is a single-byte character
  set language. In DBCS language environments, `LENB` counts each double-byte character as 2 bytes.