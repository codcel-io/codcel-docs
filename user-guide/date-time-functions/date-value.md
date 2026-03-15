<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DATEVALUE Function

The `DATEVALUE` function in Excel is used to convert a date represented as text into an Excel serial number. This serial
number allows the text-based date to be used in mathematical operations or date/time functions within Excel. The
resulting number corresponds to the number of days since January 1, 1900 (or January 1, 1904, depending on the date
system used).

## Syntax

    DATEVALUE(date_text)

- `date_text`: A text string representing a date. The text can be entered in quotes (e.g., `"2023-10-31"`) or referenced
  from a cell containing the date text. The format must be recognizable as a valid date format in Excel, based on the
  regional settings of your system.

## Returns

The `DATEVALUE` function returns a numeric value representing the date. This value corresponds to the serial number used
internally by Excel to represent dates. It can be formatted as a date by applying a date format in the cell settings.

## Key Features

- **Date Conversion**: Converts text-based dates into values that Excel can process in calculations.
- **Versatility**: Works with a variety of date formats recognized by Excel.
- **Date Arithmetic**: Enables date-related calculations on dates originally stored as text.

## Example

Suppose you have the text `"2023-10-31"` in cell `A1` and wish to convert it into a date serial number.

    =DATEVALUE("2023-10-31")  

Or, if the text is in a cell reference:

    =DATEVALUE(A1)

If Excel uses the 1900 date system, this will return `45148`, representing October 31, 2023. Applying a date format to
the cell will display it as `10/31/2023`.

## Notes

- If the `date_text` is not a valid date, Excel will return a `#VALUE!` error.
- The `DATEVALUE` function only converts text dates. It does not work with actual date values or timestamps.
- Time information in `date_text` is ignored, meaning only the date portion is converted.

## Practical Use Cases

1. **Importing Data**: Converting imported text-based dates into usable Excel date values.
2. **Data Formatting**: Normalizing inconsistent date formats stored as text.
3. **Date Calculations**: Enabling arithmetic operations on text-based dates, such as finding differences or adding
   days.

### Example with Date Manipulation:

Assume cell `A1` contains `"2023-10-31"`. You can add 7 days to this date as follows:

    =DATEVALUE(A1) + 7

This will output `45155`, corresponding to November 7, 2023, when formatted as a date.

### Summary

The `DATEVALUE` function is a simple yet powerful tool in Excel for transforming text-based date entries into functional
date values, unlocking the potential for complex date calculations and formatting. Ensure that the input date format
aligns with your system's regional settings for accurate conversion.