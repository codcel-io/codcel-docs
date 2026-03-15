<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TIME Function

The `TIME` function in Excel is used to create a time value by specifying the hour, minute, and second. It is
particularly useful for constructing time values from individual hour, minute, and second inputs, or when manipulating
time values through dynamic calculations.

## Syntax

    TIME(hour, minute, second)

- `hour`: A numeric value representing the hour component of the time. It can be any integer, and values exceeding 23
  will adjust the day accordingly.
- `minute`: A numeric value denoting the minutes. Similar to the hour component, values beyond 59 adjust the hour and
  possibly the day.
- `second`: A numeric value representing the seconds. Values beyond 59 cause similar adjustments to the minute and hour
  components.

## Returns

The `TIME` function returns a time value formatted according to the spreadsheet's time settings. It is compatible with
time comparisons, calculations, or further analytical functions.

## Key Features

- **Dynamic Time Construction**: Allows for the explicit creation of time values from separate hour, minute, and second
  inputs.
- **Flexible Input Handling**: Accepts logical minute and second values that automatically accommodate typical
  overflows, ensuring correct hour and minute calculations.
- **Consistency in Time Calculations**: Ensures accuracy by correctly adjusting minutes, hours, and potentially days,
  preventing common time errors.

## Example

Suppose you want to create a time for 2:30:45 PM.

    =TIME(14, 30, 45)

This formula constructs the time value for 2:30:45 PM.

If you supply `minute` or `second` values that exceed their typical range:

    =TIME(12, 70, 90)

This formula adjusts the input to correctly produce 1:11:30 PM, since 70 minutes add an extra hour and 90 seconds add a
minute and a half a minute, leading to the adjustment.

## Notes

- The `TIME` function is invaluable when times are broken into components or derived from computations.
- It automatically adjusts overflows beyond typical hour, minute, or second values, ensuring time validity within
  calculations.
- Use this function when needing precision in time creation from separate numerical inputs.

## Dynamic Adjustments

- Hour Overflow: Adding hours over 23 automatically rolls over to the subsequent day, adjusting hours accordingly.
- Minute and Second Adjustments: Additional minutes or seconds that extend beyond their typical maximum are
  appropriately adjusted to form an accurate time.

The `TIME` function in Excel facilitates precise time handling, essential for accurate data analysis and calculations
involving scheduled events or time-sensitive data.