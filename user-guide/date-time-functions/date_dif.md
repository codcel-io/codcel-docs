<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DATEDIF Function

The `DATEDIF` function in Excel is used to calculate the difference between two dates. This difference can be returned
in years, months, or days, based on the specified unit. Despite being a hidden function, `DATEDIF` remains a powerful
tool for date calculations, especially when handling age calculations or determining elapsed time between two dates.

## Syntax

    DATEDIF(start_date, end_date, unit)

- `start_date`: The initial date from which the difference is calculated. Entered as a date, cell reference, or aligned
  text with a date format.
- `end_date`: The date up to which the difference is calculated. Entered similarly to `start_date`.
- `unit`: A string that determines the unit for the difference result. It can be `"Y"` for years, `"M"` for months,
  `"D"` for days, `"MD"` for days ignoring months and years, `"YM"` for months ignoring days and years, or `"YD"` for
  days ignoring years.

## Returns

The `DATEDIF` function returns a numeric value that represents the difference between the two dates based on the
selected unit. Each unit provides a different aspect of the interval, such as total days, complete months, or full
years.

## Key Features

- **Versatile Date Calculations**: `DATEDIF` is suited for calculating the period between two dates in varied terms of
  days, months, or years.
- **Comprehensive Units**: Provides flexibility with various units that ignore different parts of the date, offering
  more nuanced interval analyses.
- **Legacy Functionality**: Although not included in newer Excel function menus, `DATEDIF` is still supported across
  many Excel versions.

## Example

Suppose you want to calculate the number of complete months between January 1, 2020, and March 10, 2023.

    =DATEDIF("2020-01-01", "2023-03-10", "M")

This formula calculates the number of complete months between the two dates, which would return `38`.

## Notes

- `DATEDIF` does not appear in the `Insert Function` dialog but can be used directly in formulas.
- Ensure `start_date` is less than or equal to `end_date`, otherwise the function will return an error.

## Supported Units

The `unit` parameter is critical in determining the calculation result. Below are detailed explanations of each unit:

## 1. Year Calculations

- `"Y"`: Computes full year differences. Useful for age calculations.

## 2. Month Calculations

- `"M"`: Computes full month differences between the start and end dates.

## 3. Day Calculations

- `"D"`: Calculates the total number of days between start and end dates.

## 4. Mixed Calculations

- `"MD"`: Determines the day difference, ignoring the months and years.
- `"YM"`: Finds the difference in months, ignoring days and years.
- `"YD"`: Computes day differences ignoring the year component.

Dynamic Calculations:

Utilize the function to adapt to various date-related scenarios by selecting the appropriate unit, offering precision or
generalization as required by the analysis.

Summary:
The `DATEDIF` function is a versatile tool for extracting precise temporal differences in Excel, accommodating complex
date interval calculations.