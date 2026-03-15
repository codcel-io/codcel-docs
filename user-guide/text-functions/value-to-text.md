<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# VALUETOTEXT Function

The `VALUETOTEXT` function in Excel is used to convert a value into text. This function can take any type of value (
e.g., numbers, errors, Booleans, or text) and return it as text, making it useful for displaying values in string format
for reporting, concatenation, or debugging purposes.

## Syntax

    VALUETOTEXT(value, [format])

- `value`: The value you want to convert into text. This can be any type of value (number, text, Boolean, error, etc.).
- `format` (optional): Specifies the output style. It can be:
    - `0` or omitted: Returns simple text, where strings are not enclosed in quotation marks.
    - `1`: Returns detailed text, where strings are enclosed in quotation marks and formatted for more explicit
      interpretation.

## Returns

The `VALUETOTEXT` function always returns the input value as text, regardless of its original data type.

## Key Features

- Converts any value into text for flexibility in formulas or reports.
- Supports both simple and detailed formats based on the optional `format` argument.

## Example

### Example 1: Converting a number to text

If `A1` contains the numerical value `1234`, the formula:

    =VALUETOTEXT(A1)

Returns: `"1234"` (as text).

---

### Example 2: Converting a Boolean value

If `A1` contains the Boolean value `TRUE`, the formula:

    =VALUETOTEXT(A1, 0)

Returns: `"TRUE"`.

---

### Example 3: Using the detailed format

If `A1` contains the string `Excel`, the formula:

    =VALUETOTEXT(A1, 1)

Returns: `"Excel"` (with quotations included).

---

### Example 4: Converting an error value

If a cell contains the error `#DIV/0!`, the formula:

    =VALUETOTEXT(A1)

Returns: `"#DIV/0!"` (as text).

## Notes

- The `VALUETOTEXT` function does not modify the actual value—it simply converts it into text for display or further
  processing.
- The optional `format` argument provides more flexibility in how the text is outputed. Use `1` when you need to
  represent data explicitly, such as in structured processing or JSON-like applications.

## Practical Use Cases

- **Debugging Formulas**: Use `VALUETOTEXT` to display intermediate results or identify incorrect values in formulas.
- **Reporting**: Generate text-based reports with converted values for easier interpretation.
- **Dynamic Concatenation**: Combine values of different types into a single text string while ensuring proper type
  conversion.