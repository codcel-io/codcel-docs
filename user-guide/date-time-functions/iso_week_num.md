<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ISOWEEKNUM Function

The `ISOWEEKNUM` function in Excel is utilized to derive the ISO 8601 week number for a specific date, according to
international standards. This function is particularly useful for businesses, reporting, and any scenarios where weekly
data classification is required.

## Syntax

    ISOWEEKNUM(date)

- `date`: A date value for which you want to determine the ISO week number. It can be input as a date serial number,
  date text, or a result from other date functions like `DATE`.

## Returns

The `ISOWEEKNUM` function returns an integer from 1 to 53, representing the ISO week of the year for the given date.
Weeks start with Monday and the first week includes the first Thursday of the year.

## Key Features

- **ISO Standard Compliance**: Calculates the week number based on the ISO 8601 standard, which is recognized
  internationally.
- **Consistent Week Calculations**: Utilizes a year-starting logic where the first week includes the year's first
  Thursday.

## Example

Suppose you wish to find the ISO week number for October 25, 2023.

    =ISOWEEKNUM(DATE(2023, 10, 25))

This formula calculates the ISO week number for October 25, 2023, and returns `43`, indicating it is the 43rd week of
the year according to ISO standards.

## Notes

- The `ISOWEEKNUM` function is crucial when aligning data to international week standards, making it indispensable for
  global reporting and scheduling.
- This function helps in tracking weekly metrics, comparing weekly data across different years, or synchronizing weekly
  schedules.
- The `date` must be a valid Excel date; otherwise, the formula might return a `#VALUE!` error.

## Advantages

- **Global Standardization**: Ensures compatibility and consistency across international datasets by following ISO 8601.
- **Data Stratification**: Facilitates data organization into weekly buckets, enhancing trend analysis and comparative
  studies.

The `ISOWEEKNUM` function in Excel is an essential tool for anyone needing reliable and standardized week numbering for
accurate data analysis and reporting.