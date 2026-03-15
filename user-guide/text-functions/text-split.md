<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    TEXTSPLIT(text, col_delimiter, [row_delimiter], [ignore_empty], [match_mode], [pad_with])

- **text**: The text string to split into multiple cells.
- **col_delimiter**: The delimiter used to determine where to split the text into columns.
- **row_delimiter**: *(Optional)* The delimiter used to determine where to split the text into rows.
- **ignore_empty**: *(Optional)* Boolean value indicating whether to ignore empty values. Defaults to `TRUE`.
- **match_mode**: *(Optional)* Can be set to `0` (default) for case-sensitive matching or `1` for case-insensitive
  matching.
- **pad_with**: *(Optional)* Value used to fill empty cells if the splitting results in an uneven distribution.

### Description:

The `TEXTSPLIT` function in Excel is used to split a text string into multiple cells based on a specified column
delimiter, row delimiter, or both. It is useful for breaking down text data into structured parts, such as separating
values in a CSV or parsing delimited strings from other data sources.

This function simplifies text manipulation and enables easy analysis of structured data in Excel.

### Examples:

1. `=TEXTSPLIT("A,B,C", ",")`  
   Result: Spreads `"A"`, `"B"`, and `"C"` into separate cells horizontally across three columns.

2. `=TEXTSPLIT("A|B|C|D", "|", , FALSE)`  
   Result: Splits into columns while retaining empty values, i.e., treats `||` as `" "`.

3. `=TEXTSPLIT("A B C D", " ", " ", TRUE)`  
   Result: Splits into both rows and columns where spaces occur, ignoring blank values.

4. `=TEXTSPLIT("Row1,Row2,Row3", ",", CHAR(10))`  
   Result: Splits `"Row1", "Row2", "Row3"` into rows across cells vertically.

### Notes:

- The `TEXTSPLIT` function can be combined with functions like `TRIM`, `SUBSTITUTE`, or `TEXTJOIN` for advanced text
  cleaning/manipulation workflows.
- Using `TEXTSPLIT` is especially powerful for handling data imports, as it can parse and convert large text strings in
  bulk.
- Use the `ignore_empty` argument to control whether multiple delimiters or trailing delimiters will create blank cells.
- Case sensitivity can be specified using the `match_mode` parameter for scenarios like parsing names or case-dependent
  text.