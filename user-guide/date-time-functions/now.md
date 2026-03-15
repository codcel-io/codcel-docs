<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# NOW Function

The `NOW` function in Excel is a versatile tool that returns the current date and time. It is particularly useful for
tasks that require timestamping, generating real-time reports, and any scenario where the exact current date and time
are crucial for calculations.

## Syntax

    NOW()

- The `NOW` function requires no arguments. It automatically provides the present date and time based on your system's
  settings.

## Returns

The `NOW` function returns the current date and time as a date serial number, which is formatted according to the
spreadsheet's date and time settings. This result can be used for timing comparisons, calculations, or other analytical
functions that require both date and time.

## Key Features

- **Real-Time Timestamp**: Always returns the current date and time, making it ideal for generating timestamps in
  dynamic reports or logs.
- **Dynamic Updating**: The returned date and time will automatically update whenever the worksheet is opened or
  recalculated.
- **Integration with Calculations**: Can be combined with other functions for computing durations, time intervals, and
  project timelines relative to the current moment.

## Example

Suppose you want to calculate the number of hours remaining until the end of the day:

    =TIME(23, 59, 59) - NOW()

This formula computes the number of hours from the current time until 11:59:59 PM of the current day.

## Notes

- The `NOW` function is ideal for timestamping tasks where both the date and time are needed.
- It updates automatically, which can be both a benefit and a consideration, especially for work that relies on fixed
  timestamps for record-keeping.

## Dynamic Date and Time Comparison

- **Calculations with NOW**: You can use the `NOW` function to dynamically calculate durations between events or time
  points. For example, `=NOW() - DATE(2020, 1, 1) - TIME(0, 0, 0)` gives the number of days and time elapsed since
  midnight on January 1, 2020.
- **Time Management**: In time-sensitive schedules, `NOW` helps in tracking progress against exact timestamps,
  facilitating timely responses to scheduling changes.

The `NOW` function in Excel enhances real-time data processing and reporting by ensuring that both the current date and
time are always considered, thereby improving accuracy and relevancy of data.