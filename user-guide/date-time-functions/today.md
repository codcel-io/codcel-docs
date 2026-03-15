<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TODAY Function

The `TODAY` function in Excel is a simple, yet powerful tool that returns the current date. It is particularly useful
for keeping track of deadlines, generating dynamic reports, and any scenario where the current date is crucial for
computations.

## Syntax

    TODAY()

- The `TODAY` function requires no arguments. It simply updates the cell to the current date based on your system's date
  settings.

## Returns

The `TODAY` function returns the current date as a date serial number, which is formatted according to the spreadsheet's
date settings. This number can be utilized for date comparisons, calculations, or other analytical functions.

## Key Features

- **Automatic Date Retrieval**: Always returns the current date, making it ideal for generating up-to-date timestamps in
  reports or logs.
- **Dynamic Updating**: The returned date will automatically update each day when the worksheet is opened or
  recalculated.
- **Integration with Calculations**: Can be combined with other functions for computing durations, deadlines, and
  project timelines relative to the current date.

## Example

Suppose you want to calculate the number of days remaining until the end of the year:

    =DATE(YEAR(TODAY()), 12, 31) - TODAY()

This formula computes the number of days from today until December 31st of the current year.

## Notes

- The `TODAY` function is ideal when only the date component is needed without the time.
- It updates automatically, which can be both an advantage and a consideration, especially for historical data analysis,
  where static dates might be preferred.

## Dynamic Date Comparison

- **Calculations with TODAY**: You can use the `TODAY` function to dynamically calculate days between events or
  deadlines. For example, `=TODAY() - DATE(2020, 1, 1)` gives the number of days since January 1, 2020.
- **Project Management**: In project schedules, `TODAY` helps in tracking the current progress against timelines,
  facilitating agile responses to schedule changes.

The `TODAY` function in Excel enhances real-time data processing and reporting by ensuring that the current date is
always considered, thereby improving data accuracy and relevance.