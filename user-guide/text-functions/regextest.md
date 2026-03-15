<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    REGEXTEST(text, regular_expression)

- **text**: The input text string you want to test against the regular expression pattern.
- **regular_expression**: The regular expression pattern used to test for a match.

### Description:

The `REGEXTEST` function tests whether a text string matches a specified regular expression pattern. It returns `TRUE`
if the pattern is found anywhere within the text, and `FALSE` if no match is found.

This function is useful for validating text formats (such as email addresses, phone numbers, or postal codes),
filtering data based on patterns, and performing conditional logic that depends on whether text conforms to a specific
structure. Unlike `REGEXEXTRACT`, which returns the matched text, `REGEXTEST` simply confirms whether a match exists.

### Examples:

1. `=REGEXTEST("Order #12345 placed", "[0-9]+")`
    - Returns `TRUE` (the text contains one or more digits).
2. `=REGEXTEST("Hello World", "^[A-Z]")`
    - Returns `TRUE` (the text starts with an uppercase letter).
3. `=REGEXTEST("user@example.com", "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}")`
    - Returns `TRUE` (the text contains a valid email address pattern).
4. `=REGEXTEST("No numbers here", "\d+")`
    - Returns `FALSE` (the text does not contain any digits).
5. `=REGEXTEST(A1, "^INV-\d{4}-\d+$")`
    - Returns `TRUE` if cell A1 contains text matching the invoice pattern (e.g., `"INV-2024-0987"`), `FALSE` otherwise.

### Notes:

- The `regular_expression` argument must be a valid regular expression. If the pattern is invalid, a `#VALUE!` error is
  returned.
- `REGEXTEST` checks whether the pattern matches anywhere in the text, not necessarily the entire string. To match the
  entire string, use anchors `^` (start) and `$` (end) in the pattern (e.g., `"^hello$"` matches only the exact string
  `"hello"`).
- The function is case-sensitive by default. To perform a case-insensitive match, prepend the pattern with `(?i)` (e.g.,
  `"(?i)hello"` matches `"Hello"`, `"HELLO"`, and `"hello"`).
- `REGEXTEST` returns a boolean (`TRUE` or `FALSE`), making it ideal for use inside `IF`, `FILTER`, `SUMPRODUCT`, and
  other functions that accept logical conditions.
- This function is available in Microsoft Excel 365 (starting late 2024) and in Google Sheets. In older versions of
  Excel, similar functionality can be achieved by combining `FIND`, `SEARCH`, `ISNUMBER`, and wildcard patterns, or by
  using VBA / Office Scripts. Codcel supports `REGEXTEST` directly.
- Related functions include `REGEXEXTRACT` (extracts the first matching substring) and `REGEXREPLACE` (replaces text
  matching a pattern).
- It can be combined with functions like `IF`, `FILTER`, `COUNTIF`, or `SUMPRODUCT` for advanced pattern-based data
  analysis workflows.