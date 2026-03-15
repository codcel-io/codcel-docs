<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SEARCHB(find_text, within_text, [start_num])

- **find_text**: The text you want to find. This can be a single character or a string. Wildcard characters `*` and `?` are supported.
- **within_text**: The text in which you want to search for the `find_text`.
- **start_num** (optional): The byte position in `within_text` at which to start the search. The default is 1, which starts at the first byte.

### Description:

The `SEARCHB` function in Excel locates one text string within another and returns the starting position measured in
bytes rather than characters. This distinction is important when working with double-byte character set (DBCS)
languages such as Japanese, Chinese, and Korean, where a single character can occupy two bytes. In single-byte
character set (SBCS) languages such as English, `SEARCHB` behaves identically to the `SEARCH` function because each
character is one byte.

Unlike the `FINDB` function, `SEARCHB` is case-insensitive — it does not distinguish between uppercase and lowercase
letters. It also supports wildcard characters (`*` to match any number of characters and `?` to match a single
character). If you need a case-sensitive byte-based search, use the `FINDB` function instead.

### Examples:

1. `=SEARCHB("World", "Hello World")`
    - Returns: `7`
      (In an SBCS environment, "World" starts at byte 7, the same position as the character position.)
2. `=SEARCHB("cat", "Concatenation")`
    - Returns: `4`
      (The case-insensitive search finds "cat" starting at byte 4 in "Concatenation".)
3. `=SEARCHB("CAT", "Concatenation")`
    - Returns: `4`
      (The search is case-insensitive; "CAT" matches "cat" within "Concatenation" at byte 4.)
4. `=SEARCHB("B", "AABBCC", 3)`
    - Returns: `3`
      (Starting the search at byte position 3, the first "B" is found at byte 3.)
5. `=SEARCHB("c*n", "Concatenation")`
    - Returns: `4`
      (The wildcard `*` matches any number of characters between "c" and "n".)

### Notes:

- The `SEARCHB` function is case-insensitive. Use `FINDB` if you need a case-sensitive byte-based search.
- If `find_text` is not found within `within_text`, the function returns a `#VALUE!` error. You can wrap `SEARCHB`
  in an `IFERROR` function to handle this gracefully.
- In SBCS languages (e.g., English), `SEARCHB` returns the same results as `SEARCH` because each character equals one
  byte. The difference only becomes apparent in DBCS languages where characters may occupy two bytes.
- The `start_num` argument counts bytes, not characters. When working with DBCS text, be mindful that a double-byte
  character occupies positions for two bytes.
- `SEARCHB` supports wildcard characters: use `*` to match any sequence of characters and `?` to match any single
  character. For exact-match byte-position searches without wildcards, use `FINDB`.
- For character-based position searching (rather than byte-based), use the `SEARCH` function.
- The `SEARCHB` function is equivalent to `SEARCH` in Excel when the default language setting is a single-byte character
  set language. In DBCS language environments, `SEARCHB` counts each double-byte character as 2 bytes.