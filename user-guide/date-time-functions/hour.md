<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# HOUR Function

The `HOUR` function in Excel is used to extract the hour from a given time value. This function is particularly useful
in scenarios where you need to analyze or sort data based on the hour component of time.

## Syntax

    HOUR(time)

- `time`: A time value from which the hour is to be extracted. This can be a time in Excel's time format, a result of a
  formula that returns a time, or a reference to a cell containing a time.

## Returns

The `HOUR` function returns an integer representing the hour portion of a time, ranging from 0 (12:00 AM) to 23 (11:00
PM).

## Key Features

- **Time Component Extraction**: Simplifies the process of isolating the hour from a complete time value for further
  data analysis.
- **Ease of Use**: Can directly use cell references or time functions as input to derive the hour component.
- **Integration with Other Functions**: Useful in conjunction with other time functions for comprehensive time
  manipulation and analysis.

## Example

Suppose you have a time value in cell `B1` which is `15:30`.

    =HOUR(B1)

This formula will return `15`, as the time corresponds to 3:00 PM.

Alternatively, you can directly specify the time using the `TIME` function:

    =HOUR(TIME(15, 30, 0))

This formula also returns `15`.

## Notes

- The `HOUR` function is essential when segregating or organizing data based on the hour attribute.
- It simplifies reporting and analytical tasks that require hour-based groupings or trends.
- Ensure the input time is in a recognized Excel time format to avoid errors.

The `HOUR` function effectively enhances your capability to analyze and manage data chronologically by focusing on the
hourly aspect, pivotal for operational, scheduling, or activity-based data assessments.