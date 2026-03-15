<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TIMEVALUE Function

The `TIMEVALUE` function in Excel is used to convert a text representation of a time into a serial number that Excel
recognizes as a valid time. This is particularly useful when working with time values stored as text that need to be
converted for calculations or formatting.

## Syntax

    TIMEVALUE(time_text)

- `time_text`: A string representing a time in any valid Excel time format, such as `"12:30 PM"` or `"23:15"`. This can
  also be a reference to a cell containing a text-formatted time.

## Returns

The `TIMEVALUE` function returns a decimal number between `0` and `0.99988426`, representing the time as a fraction of
the day (e.g., `0.5` represents 12:00 PM because it is half of the day).

## Key Features

- **Text Conversion**: Converts time stored as text into usable numeric time values.
- **Calculation Compatibility**: Enables mathematical operations on times stored as text.
- **Integration**: Works seamlessly with other Excel time/date functions for advanced scheduling or analysis.

## Example

Suppose you have a time stored as text in cell `A1` with the value `"3:45 PM"`.

    =TIMEVALUE(A1)

This formula will return `0.65625`, as `3:45 PM` is approximately 65.625% through the day.

Alternatively, you can directly input the text:

    =TIMEVALUE("15:45")

This will also return `0.65625`.

## Notes

- The function is essential when importing data from external sources where times are stored as text.
- If the input `time_text` is not in a recognizable format, the function will return a `#VALUE!` error.
- The resulting decimal can be formatted as time using Excel's time or custom formatting options for easier
  interpretation.

The `TIMEVALUE` function is a powerful tool for data preparation and ensures that time values in text format are readily
usable in calculations and analyses.