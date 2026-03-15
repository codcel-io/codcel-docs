<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    PHONETIC(reference)

- **reference**: A cell reference or range of cells containing text strings with furigana (phonetic) information.

### Description:

The `PHONETIC` function in Excel extracts the furigana (phonetic guide) characters from a text string in a cell. Furigana
are small kana characters (hiragana or katakana) placed above or beside kanji characters in Japanese text to indicate
their pronunciation. When Japanese text is entered via an input method editor (IME) in Excel, the phonetic reading used
during input is stored as metadata alongside the displayed text.

For example, if a cell contains the kanji `東京` (Tokyo) and it was entered using an IME, `PHONETIC` will return the
phonetic reading such as `トウキョウ` (in katakana) or `とうきょう` (in hiragana), depending on the furigana settings.

If the referenced cell contains only non-Japanese text or text without furigana data, the function returns the original
text unchanged.

### Examples:

1. `=PHONETIC(A1)`
    - If A1 contains `東京` entered via an IME, returns `トウキョウ` (the katakana phonetic reading stored with the text).
2. `=PHONETIC(A1:A3)`
    - Concatenates the furigana readings from all cells in the range A1 through A3 into a single string.
3. `=PHONETIC(B2)`
    - If B2 contains `田中` (Tanaka), returns `タナカ` (the phonetic reading associated with the kanji).
4. `=PHONETIC(C1)`
    - If C1 contains `Hello` (no furigana data), returns `"Hello"` (the original text is returned unchanged).

### Notes:

- The `PHONETIC` function is specifically designed for Japanese text processing and relies on furigana metadata stored by
  Excel when text is entered using a Japanese Input Method Editor (IME).
- If the cell does not contain furigana information (e.g., text was pasted or typed without an IME), the function returns
  the original cell text as-is.
- When a range of cells is specified, `PHONETIC` concatenates the phonetic readings of all cells in the range into a
  single text string.
- The type of phonetic characters returned (hiragana or katakana) depends on the furigana settings configured for the
  cell. By default, Excel typically uses katakana.
- This function is most useful in Japanese-language spreadsheets for tasks such as sorting names by pronunciation,
  creating reading aids, or extracting pronunciation data for further processing.
- The `PHONETIC` function has no direct inverse function. To set or modify furigana, use the Excel UI (Home > Phonetic
  Guide) rather than a formula.
- In non-Japanese locales or when working with text that does not have furigana metadata, this function simply returns
  the original text and has no visible effect.