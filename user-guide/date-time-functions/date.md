<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DATE Function

The `DATE` function in Excel is utilized to create a date value by specifying the year, month, and day. It is
particularly useful for constructing dates from individual year, month, and day inputs or when manipulating date values
through dynamic calculations.

## Syntax

    DATE(year, month, day)

- `year`: A positive or negative integer representing the year component of the date.
- `month`: An integer denoting the month (1 to 12). Values outside this range adjust the year and month accordingly.
- `day`: An integer representing the day of the month. Similar to the month parameter, values beyond the month range
  impact the resulting month and year dynamically.

## Returns

The `DATE` function returns a date value formatted according to the spreadsheet's date settings. It is compatible with
date comparisons, calculations, or further analytical functions.

## Key Features

- **Dynamic Date Construction**: Allows for the explicit creation of date values from separate year, month, and day
  inputs.
- **Flexible Input Handling**: Accepts logical month and day values that automatically accommodate typical overflows
  such as leap years and month-end variations.
- **Error-free Date Calculations**: Ensures date integrity by correctly rolling months and years, thus preventing common
  date errors.

## Example

Suppose you want to create a date for December 25th, 2023.

    =DATE(2023, 12, 25)

This formula constructs the date value for December 25, 2023.

If you supply `month` or `day` values that exceed their typical range:

    =DATE(2023, 15, 32)

This formula adjusts the input to correctly produce March 2, 2024, since January 32, 2024, corresponds to March 2, after
adding the extra days and months.

## Notes

- The `DATE` function is invaluable when dates are broken into components or derived from computations.
- It automatically adjusts leap year scenarios, ensuring date validity within calculations.
- Use this function when needing precision in date creation from separate numerical inputs.

## Dynamic Adjustments

- Month Overflow: Adding months over 12 automatically rolls over to the subsequent year with correct month adjustments.
- Day Adjustments: Additional days that extend beyond the month's last day are appropriately added to form an accurate
  date.

The `DATE` function in Excel facilitates precise date handling, essential for accurate data analysis and calculations
involving timeline events or schedules.