<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# MINUTE Function

The `MINUTE` function in Excel is used to extract the minute component from a given time value. It is particularly
useful in scenarios where you need to analyze, sort, or perform calculations based on the minute part of time entries.

## Syntax

    MINUTE(time)

- `time`: A time value from which the minute number is to be extracted. This can be a time in Excel's time
  format, a result of a formula that returns a time, or a reference to a cell containing a time.

## Returns

The `MINUTE` function returns an integer representing the minute portion of a time, ranging from 0 to 59.

## Key Features

- **Time Component Extraction**: Simplifies the process of isolating the minute from a complete time value for further
  data analysis.
- **Ease of Use**: Can directly use cell references or time functions as input to derive the minute component.
- **Integration with Other Functions**: Useful in conjunction with other time functions for comprehensive time
  manipulation and analysis.

## Example

Suppose you have a time value in cell `B1` which is `14:45:30`.

    =MINUTE(B1)

This formula will return `45`, as it is the minute part of the time `14:45:30`.

Alternatively, you can directly specify the time using the `TIME` function:

    =MINUTE(TIME(14, 45, 30))

This formula also returns `45`.

## Notes

- The `MINUTE` function is essential when analyzing data that requires focus on minute-specific details, such as
  scheduling or timing-related calculations.
- It simplifies reporting and analytical tasks that require minute-based distinctions.
- Ensure the input time is in a recognized Excel time format to avoid errors.

The `MINUTE` function effectively enhances your capability to analyze and manage data that is time-sensitive by focusing
on the minute aspect, vital for time-tracking, event management, or performance measurement tasks.