<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

UNICODE(text)

- **text**: A text string, where the function will return the Unicode character number of the first character in the
  string.

### Description:

The `UNICODE` function in Excel returns the numeric Unicode value of the first character in a text string. It is useful
for identifying the Unicode number for specific characters and working with text encoded in Unicode format.

### Examples:

1. `=UNICODE("A")`  
   Result: `65`. Returns the Unicode number for the letter `A`.
2. `=UNICODE("☃")`  
   Result: `9731`. Provides the Unicode value for the snowman symbol.
3. `=UNICODE("😄")`  
   Result: `128516`. Returns the Unicode value for the smiling face emoji.
4. `=UNICODE("€")`  
   Result: `8364`. Outputs the Unicode number for the euro currency symbol.

### Notes:

- The `UNICODE` function focuses on the first character of the input text string. To evaluate another position in a
  string, extract the relevant character first (e.g., using the `MID` or `LEFT` function).
- This function pairs naturally with `UNICHAR` to perform the reverse process: converting a Unicode number back into its
  corresponding character.
- If the input text is empty, the `UNICODE` function will return a `#VALUE!` error.
- Non-printable or unsupported characters in your system may not display but will still have valid Unicode values.