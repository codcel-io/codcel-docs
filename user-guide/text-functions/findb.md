<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    FINDB(find_text, within_text, [start_num])

- **find_text**: The text you want to find. This can be a single character or a string.
- **within_text**: The text in which you want to search for the `find_text`.
- **start_num** (optional): The byte position in `within_text` at which to start the search. The default is 1, which starts at the first byte.

### Description:

The `FINDB` function in Excel locates one text string within another and returns the starting position measured in
bytes rather than characters. This distinction is important when working with double-byte character set (DBCS)
languages such as Japanese, Chinese, and Korean, where a single character can occupy two bytes. In single-byte
character set (SBCS) languages such as English, `FINDB` behaves identically to the `FIND` function because each
character is one byte.

Like the `FIND` function, `FINDB` is case-sensitive — it distinguishes between uppercase and lowercase letters. It
does not support wildcard characters. If you need a case-insensitive byte-based search, use the `SEARCHB` function
instead.

### Examples:

1. `=FINDB("World", "Hello World")`
    - Returns: `7`
      (In an SBCS environment, "World" starts at byte 7, the same position as the character position.)
2. `=FINDB("cat", "Concatenation")`
    - Returns: `4`
      (The lowercase "cat" begins at byte 4 in "Concatenation".)
3. `=FINDB("Cat", "Concatenation")`
    - Returns: `#VALUE!`
      (The search is case-sensitive; "Cat" with an uppercase "C" does not appear in "Concatenation".)
4. `=FINDB("B", "AABBCC", 3)`
    - Returns: `3`
      (Starting the search at byte position 3, the first "B" is found at byte 3.)

### Notes:

- The `FINDB` function is case-sensitive. Use `SEARCHB` if you need a case-insensitive byte-based search.
- If `find_text` is not found within `within_text`, the function returns a `#VALUE!` error. You can wrap `FINDB`
  in an `IFERROR` function to handle this gracefully.
- In SBCS languages (e.g., English), `FINDB` returns the same results as `FIND` because each character equals one
  byte. The difference only becomes apparent in DBCS languages where characters may occupy two bytes.
- The `start_num` argument counts bytes, not characters. When working with DBCS text, be mindful that a double-byte
  character occupies positions for two bytes.
- `FINDB` does not support wildcard characters (`*`, `?`). For wildcard-based byte-position searches, use `SEARCHB`.
- For character-based position finding (rather than byte-based), use the `FIND` function.
- The `FINDB` function is equivalent to `FIND` in Excel when the default language setting is a single-byte character
  set language. In DBCS language environments, `FINDB` counts each double-byte character as 2 bytes.