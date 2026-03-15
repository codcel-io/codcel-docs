<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    TEXT(value, format_text)

- **value**: The number, date, or text you wish to convert into a specific format.
- **format_text**: A text string that specifies the desired format for the `value`. Common placeholders are used to
  represent dates, times, and numeric formats.

### Description:

The `TEXT` function in Excel is used to format numbers, dates, and times as text in a specific format. It takes a value
and converts it into a user-defined textual representation based on the provided format string. This function is
especially useful for custom formatting of numeric and date/time values in dashboards, reports, or templates.

### Examples:

1. `=TEXT(1234.567, "#,##0.00")`  
   Result: `1,234.57`. Formats the number with commas as thousand separators and two decimal places.

2. `=TEXT(TODAY(), "dd/mm/yyyy")`  
   Result (if today is October 15, 2023): `15/10/2023`. Converts the date returned by `TODAY()` into the specified
   format.

3. `=TEXT(0.56, "0%")`  
   Result: `56%`. Converts a decimal value into a percentage format.

4. `=TEXT(4500, "$#,##0")`  
   Result: `$4,500`. Formats the number as currency, including thousands separator and no decimal places.

5. `=TEXT(NOW(), "hh:mm AM/PM")`  
   Result (if the current time is 2:30 PM): `02:30 PM`. Formats the current time in 12-hour time format with an AM/PM
   designation.

6. `=TEXT(12345.6789, "0.00E+00")`  
   Result: `1.23E+04`. Converts the number into scientific (exponential) notation.

7. `=TEXT(DATE(2023,10,15), "dddd, mmmm dd, yyyy")`  
   Result: `Sunday, October 15, 2023`. Formats the date in a long-text format.

### Notes:

- The `TEXT` function always returns a result as text, even if the original value is numeric or a date/time.
- If the format string in `format_text` is invalid, Excel will return a `#VALUE!` error.
- Format codes for numeric values include symbols like `#`, `0`, `%`, or `,` for patterns and separators.
- When working with dates and times, use specific placeholders like `dd` for day, `mm` for month, `yyyy` for year, and
  `hh` for hours.
- The difference between `TEXT` and native formatting (e.g., cell styles) is that `TEXT` embeds the formatted value into
  formulas and outputs it explicitly as text.
- This function does not adjust for localization automatically—ensure the format aligns with your region's standards if
  needed.
- Combine `TEXT` with other functions, such as `CONCAT`, `IF`, or `VALUE`, for dynamic formatting in complex workflows.