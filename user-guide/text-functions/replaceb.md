<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    REPLACEB(old_text, start_num, num_bytes, new_text)

- **old_text**: The original text string in which you want to replace characters. This can be a direct string, a cell reference, or the result of another function.
- **start_num**: The byte position in `old_text` where the replacement begins. The first byte in `old_text` is 1.
- **num_bytes**: The number of bytes in `old_text` that you want to replace with `new_text`.
- **new_text**: The text string that will replace the specified bytes in `old_text`. This can be an empty string (`""`) to delete characters.

### Description:

The `REPLACEB` function in Excel replaces part of a text string with a different text string, based on the number of
bytes you specify rather than the number of characters. This distinction is important when working with double-byte
character set (DBCS) languages such as Japanese, Chinese, and Korean, where a single character can occupy two bytes. In
single-byte character set (SBCS) languages such as English, `REPLACEB` behaves identically to the `REPLACE` function
because each character is one byte.

Unlike the `SUBSTITUTE` function, which finds and replaces specific text, `REPLACEB` replaces text at a specified byte
position and length. This makes it particularly useful when you need to modify text at an exact byte position, such as
when processing structured data or fixed-width fields that contain a mix of single-byte and double-byte characters.

For example:

    REPLACEB(old_text, start_num, num_bytes, new_text) = text with bytes replaced

### Examples:

1. `=REPLACEB("HelloWorld", 6, 5, "Excel")`
    - Returns: `"HelloExcel"`
      (In an SBCS environment, replaces 5 bytes starting at byte 6, replacing "World" with "Excel".)
2. `=REPLACEB("Hello World", 7, 5, "Excel")`
    - Returns: `"Hello Excel"`
      (In an SBCS environment, replaces "World" starting at byte 7 with "Excel".)
3. `=REPLACEB("12345", 2, 3, "678")`
    - Returns: `"16785"`
      (Replaces 3 bytes starting at byte 2, replacing "234" with "678".)
4. `=REPLACEB(A1, 1, 4, "Test")`
    - Replaces the first 4 bytes of text in cell A1 with "Test".
      (In an SBCS environment, this is equivalent to `=REPLACE(A1, 1, 4, "Test")`.)
5. `=REPLACEB("Hello World", 6, 1, "")`
    - Returns: `"HelloWorld"`
      (Replaces 1 byte at position 6 with an empty string, effectively deleting the space.)

### Notes:

- In SBCS languages (e.g., English), `REPLACEB` returns the same results as `REPLACE` because each character equals one
  byte. The difference only becomes apparent in DBCS languages where characters may occupy two bytes.
- If `start_num` is less than 1, Excel will return a `#VALUE!` error.
- If `num_bytes` is negative, Excel will return a `#VALUE!` error.
- If `start_num` is greater than the byte length of `old_text`, `new_text` is appended to the end of `old_text`.
- If `num_bytes` is 0, `new_text` is inserted at the byte position specified by `start_num` without removing any
  existing bytes.
- Setting `new_text` to an empty string (`""`) effectively deletes the specified bytes from `old_text`.
- The `start_num` and `num_bytes` arguments count bytes, not characters. When working with DBCS text, be mindful
  that a double-byte character occupies positions for two bytes.
- For character-based replacement (rather than byte-based), use the `REPLACE` function.
- The `REPLACEB` function is equivalent to `REPLACE` in Excel when the default language setting is a single-byte
  character set language. In DBCS language environments, `REPLACEB` counts each double-byte character as 2 bytes.