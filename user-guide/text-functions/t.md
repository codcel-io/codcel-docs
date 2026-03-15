<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    T(value)

- **value**: The value you want to test and return as text.

### Description:

The `T` function in Excel checks whether a value is text and returns it if true. If the value is not text (e.g., a
number, date, or logical value), it will return an empty string (`""`). This function is primarily used in scenarios
where you need to extract or validate text from a mixed dataset.

### Examples:

1. `=T("Hello")`  
   Result: `"Hello"`. Since the input is already text, the function returns it as-is.

2. `=T(1234)`  
   Result: `""`. Numbers are not considered text, so an empty string is returned.

3. `=T(TRUE)`  
   Result: `""`. Logical values like `TRUE` or `FALSE` are not text, so the function returns an empty string.

4. `=T("1234")`  
   Result: `"1234"`. Even though this input looks like a number, it's treated as text because it is enclosed in
   quotation marks.

5. `=T(A1)`  
   Result: Depends on the content of cell `A1`. If the value in `A1` is text, it will be returned. Otherwise, an empty
   string will be output.

### Notes:

- The `T` function is rarely used in modern Excel because logical functions (like `IF` or `ISNUMBER`) and text
  functions (like `ISTEXT`) often offer more practical alternatives.
- It is mainly included for compatibility with older versions of Excel.
- When working with calculations involving both text and non-text values, consider using this function to filter and
  handle text values explicitly.
- If the value is blank (completely empty), `T` will return an empty string, too.