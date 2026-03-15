<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# MONTH Function

The `MONTH` function in Excel is used to extract the month from a given date value. It is particularly useful in
scenarios where you need to analyze or sort data based on the month component of dates.

## Syntax

    MONTH(date)

- `date`: A date value from which the month is to be extracted. This can be a date in Excel's date format, a
  result of a formula that returns a date, or a reference to a cell containing a date.

## Returns

The `MONTH` function returns an integer representing the month portion of a date, ranging from 1 (January) to 12 (
December).

## Key Features

- **Date Component Extraction**: Simplifies the process of isolating the month from a complete date value for further
  data analysis.
- **Ease of Use**: Can directly use cell references or date functions as input to derive the month component.
- **Integration with Other Functions**: Useful in conjunction with other date functions for comprehensive date
  manipulation and analysis.

## Example

Suppose you have a date value in cell `A1` which is `25-Dec-2023`.

    =MONTH(A1)

This formula will return `12`, as December is the 12th month.

Alternatively, you can directly specify the date using the `DATE` function:

    =MONTH(DATE(2023, 12, 25))

This formula also returns `12`.

## Notes

- The `MONTH` function is essential when segregating or organizing data based on the month attribute.
- It simplifies reporting and analytical tasks that require month-based groupings or trends.
- Ensure the input date is in a recognized Excel date format to avoid errors.

The `MONTH` function effectively enhances your capability to analyze and manage data chronologically by focusing on the
monthly aspect, pivotal for financial, operational, or seasonal data assessments.