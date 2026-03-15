<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    REGEXEXTRACT(text, regular_expression)

- **text**: The input text string from which you want to extract matching content.
- **regular_expression**: The regular expression pattern used to match and extract text. The first matching substring (or
  capture group) is returned.

### Description:

The `REGEXEXTRACT` function extracts the first substring that matches a specified regular expression pattern from a given
text string. If the regular expression contains one or more capture groups (parenthesized subexpressions), the function
returns the text matched by the first capture group. If there are no capture groups, the entire match is returned.

This function is particularly useful for parsing structured text, extracting specific patterns such as numbers, email
addresses, dates, or codes from free-form text, and performing advanced text extraction that cannot be achieved with
simpler functions like `MID`, `LEFT`, or `RIGHT`.

### Examples:

1. `=REGEXEXTRACT("Order #12345 placed", "[0-9]+")`
    - Returns `"12345"` (extracts the first sequence of digits from the text).
2. `=REGEXEXTRACT("Email: user@example.com", "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}")`
    - Returns `"user@example.com"` (extracts the email address from the text).
3. `=REGEXEXTRACT("Invoice INV-2024-0987", "INV-(\d{4})-(\d+)")`
    - Returns `"2024"` (extracts the content of the first capture group).
4. `=REGEXEXTRACT("Price: $49.99", "\$([0-9]+\.[0-9]{2})")`
    - Returns `"49.99"` (extracts the dollar amount using a capture group, excluding the `$` sign).
5. `=REGEXEXTRACT(A1, "\b[A-Z]{2,}\b")`
    - Extracts the first word consisting entirely of uppercase letters from the text in cell A1.

### Notes:

- The `regular_expression` argument must be a valid regular expression. If the pattern is invalid, a `#VALUE!` error is
  returned.
- If no match is found in the text, the function returns a `#N/A` error. Wrapping the formula in `IFERROR` can handle
  this gracefully (e.g., `=IFERROR(REGEXEXTRACT(A1, "\d+"), "No match")`).
- When the pattern contains capture groups `()`, only the content of the first capture group is returned. If no capture
  groups are defined, the entire matched substring is returned.
- The function is case-sensitive by default. To perform a case-insensitive match, prepend the pattern with `(?i)` (e.g.,
  `"(?i)hello"` matches `"Hello"`, `"HELLO"`, and `"hello"`).
- `REGEXEXTRACT` only returns the first match. To extract all matches or multiple occurrences, consider combining it with
  other functions or using helper columns.
- This function is not natively available in Microsoft Excel. It originates from Google Sheets. In Excel, similar
  functionality can be achieved by combining `MID`, `FIND`, `SEARCH`, and `LEN`, or by using VBA / Office Scripts. Codcel
  supports `REGEXEXTRACT` directly.
- Related functions include `REGEXMATCH` (tests whether text matches a pattern) and `REGEXREPLACE` (replaces text
  matching a pattern).
- It can be combined with functions like `IFERROR`, `IF`, `LEN`, or `VALUE` for advanced text processing workflows.