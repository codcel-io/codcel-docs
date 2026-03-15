<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    REGEXREPLACE(text, regular_expression, replacement)

- **text**: The input text string in which you want to perform the replacement.
- **regular_expression**: The regular expression pattern used to match text that should be replaced.
- **replacement**: The replacement text to substitute for each match. Can include backreferences such as `$1`, `$2`, etc.
  to refer to capture groups in the pattern.

### Description:

The `REGEXREPLACE` function replaces all substrings that match a specified regular expression pattern within a given text
string with a replacement string. If the regular expression contains capture groups (parenthesized subexpressions), the
replacement string can reference those groups using backreferences (`$1`, `$2`, etc.).

This function is particularly useful for advanced find-and-replace operations that go beyond simple text substitution,
such as reformatting dates, cleaning up inconsistent data, stripping unwanted characters, or restructuring text patterns.
Unlike `SUBSTITUTE`, which matches literal text, `REGEXREPLACE` matches patterns, making it far more flexible.

### Examples:

1. `=REGEXREPLACE("Order #12345 placed", "[0-9]+", "XXXXX")`
    - Returns `"Order #XXXXX placed"` (replaces the sequence of digits with `"XXXXX"`).
2. `=REGEXREPLACE("Hello   World", "\s+", " ")`
    - Returns `"Hello World"` (replaces one or more whitespace characters with a single space).
3. `=REGEXREPLACE("2024-01-15", "(\d{4})-(\d{2})-(\d{2})", "$2/$3/$1")`
    - Returns `"01/15/2024"` (reformats a date from YYYY-MM-DD to MM/DD/YYYY using capture group backreferences).
4. `=REGEXREPLACE("user@example.com", "@.*", "@newdomain.com")`
    - Returns `"user@newdomain.com"` (replaces the domain portion of an email address).
5. `=REGEXREPLACE(A1, "[^a-zA-Z0-9]", "")`
    - Removes all non-alphanumeric characters from the text in cell A1.

### Notes:

- The `regular_expression` argument must be a valid regular expression. If the pattern is invalid, a `#VALUE!` error is
  returned.
- `REGEXREPLACE` replaces all occurrences of the pattern in the text, not just the first match. This is similar to a
  global replace (`/g` flag in many regex implementations).
- The `replacement` string can include backreferences (`$1`, `$2`, etc.) to insert text captured by parenthesized groups
  in the regular expression. Use `$0` to reference the entire match.
- To insert a literal `$` in the replacement string, escape it as `$$`.
- The function is case-sensitive by default. To perform a case-insensitive replacement, prepend the pattern with `(?i)`
  (e.g., `"(?i)hello"` matches `"Hello"`, `"HELLO"`, and `"hello"`).
- If no match is found in the text, the original text is returned unchanged (no error is raised).
- This function is not natively available in Microsoft Excel. It originates from Google Sheets. In Excel, similar
  functionality can be achieved by combining `SUBSTITUTE`, `MID`, `FIND`, and `LEN`, or by using VBA / Office Scripts.
  Codcel supports `REGEXREPLACE` directly.
- Related functions include `REGEXEXTRACT` (extracts the first matching substring) and `REGEXTEST` (tests whether text
  matches a pattern).
- It can be combined with functions like `IF`, `IFERROR`, `TRIM`, or `LEN` for advanced text processing workflows.