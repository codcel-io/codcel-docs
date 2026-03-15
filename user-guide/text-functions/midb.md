<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    MIDB(text, start_num, num_bytes)

- **text**: The text string containing the characters you want to extract. This can be a direct string, a cell reference, or the result of another function.
- **start_num**: The position of the first character you want to extract, counted in bytes. The first byte in `text` is 1.
- **num_bytes**: The number of bytes to extract from the `text`, starting at `start_num`.

### Description:

The `MIDB` function in Excel returns a specific number of characters from a text string, starting at the position you
specify, based on the number of bytes rather than the number of characters. This distinction is important when working
with double-byte character set (DBCS) languages such as Japanese, Chinese, and Korean, where a single character can
occupy two bytes. In single-byte character set (SBCS) languages such as English, `MIDB` behaves identically to the
`MID` function because each character is one byte.

Its flexible parameters allow selection of any subset of the string based on byte positions, which is particularly
useful when processing text that contains a mix of single-byte and double-byte characters.

For example:

    MIDB("text", start_num, num_bytes) = extracted substring (by bytes)

### Examples:

1. `=MIDB("HelloWorld", 1, 5)`
    - Returns: `"Hello"`
      (In an SBCS environment, the first 5 bytes correspond to the first 5 characters.)
2. `=MIDB("HelloWorld", 6, 5)`
    - Returns: `"World"`
      (Starts at the 6th byte and extracts 5 bytes.)
3. `=MIDB("Excel Functions", 7, 9)`
    - Returns: `"Functions"`
      (In an SBCS environment, this is equivalent to `=MID("Excel Functions", 7, 9)`.)
4. `=MIDB(A1, 3, 4)`
    - Returns 4 bytes of text from cell A1 starting at the 3rd byte.
      (In an SBCS environment, this is equivalent to `=MID(A1, 3, 4)`.)
5. `=MIDB("Excel", 2, 10)`
    - Returns: `"xcel"`
      (If `num_bytes` exceeds the remaining byte length of the text from `start_num`, all characters from `start_num` to the end are returned.)

### Notes:

- In SBCS languages (e.g., English), `MIDB` returns the same results as `MID` because each character equals one
  byte. The difference only becomes apparent in DBCS languages where characters may occupy two bytes.
- If `start_num` is greater than the byte length of `text`, the `MIDB` function will return an empty string (`""`).
- If `start_num` is less than 1, Excel will return a `#VALUE!` error.
- If `num_bytes` is negative, Excel will return a `#VALUE!` error.
- If `num_bytes` is 0, an empty string (`""`) is returned.
- If `start_num + num_bytes - 1` exceeds the byte length of `text`, the function will return all bytes from
  `start_num` to the end of the `text`.
- The `start_num` and `num_bytes` arguments count bytes, not characters. When working with DBCS text, be mindful
  that a double-byte character occupies positions for two bytes.
- For character-based extraction (rather than byte-based), use the `MID` function.
- The `MIDB` function is equivalent to `MID` in Excel when the default language setting is a single-byte character
  set language. In DBCS language environments, `MIDB` counts each double-byte character as 2 bytes.