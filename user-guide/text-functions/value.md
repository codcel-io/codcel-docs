<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    VALUE(text)

- **text**: A text string or cell reference that represents a number formatted as text.

### Description:

The `VALUE` function in Excel converts a text string that represents a number into an actual numeric value. This can be
useful when numbers stored as text need to be used in calculations.

### Examples:

1. `=VALUE("123")`  
   Result: `123`. Converts the text string `"123"` into a numeric value.

2. `=VALUE(" 456.78 ")`  
   Result: `456.78`. Trims any extra spaces and converts the text `" 456.78 "` into a numeric value.

3. `=VALUE("$1,000")`  
   Result: `1000`. Converts the text string `"$1,000"` into a numeric value.

4. `=VALUE(A1)`  
   Result: If cell `A1` contains `"78.9"`, the function returns the numeric value `78.9`.

### Notes:

- The `VALUE` function is not always necessary in modern Excel versions, as Excel tends to handle text-numeric
  conversions automatically in many cases.
- If `text` cannot be converted into a valid number, the function will return the `#VALUE!` error.
- Common use cases include cleaning up imported data or ensuring accurate mathematical operations with numbers stored as
  text.