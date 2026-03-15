<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# YEARFRAC Function

The `YEARFRAC` function in Excel calculates the fraction of the year represented by the number of whole days between two
dates. It is commonly used in financial calculations, such as determining the proportion of a year between two dates for
interest accrual.

## Syntax

    YEARFRAC(start_date, end_date, [basis])

- `start_date`: The starting date for the calculation.
- `end_date`: The ending date for the calculation.
- `[basis]` *(optional)*: An optional argument that specifies the day count convention to be used in the calculation.  
  If omitted, the default value is `0` (US 30/360).

## Day Count Basis Options

The `basis` argument allows you to define how the days in a year are calculated. The options are:

| Value | Day Count Basis                      | Description                                                                                   |
|-------|--------------------------------------|-----------------------------------------------------------------------------------------------|
| `0`   | US (NASD) 30/360                    | Assumes 30-day months and 360-day years.                                                     |
| `1`   | Actual/Actual                       | Uses the actual number of days in the month and year.                                         |
| `2`   | Actual/360                          | Uses the actual number of days in the month, but assumes a 360-day year.                     |
| `3`   | Actual/365                          | Uses the actual number of days in the month, but assumes a 365-day year.                     |
| `4`   | European 30/360                     | Similar to US 30/360, but adjusts for end-of-month scenarios based on European standards.    |

## Returns

The `YEARFRAC` function returns a decimal number representing the fraction of a year between the `start_date` and
`end_date` based on the selected day count basis.

## Key Features

- Used for calculating partial-year interest payments, depreciation schedules, or other time-based calculations.
- Allows flexibility with its customizable day count basis to suit different financial calculations and geographic
  conventions.

## Example

### Example 1: Calculate Fraction of a Year with Default Basis

Suppose you want to calculate the fraction of the year between `01-Jan-2024` and `30-Jun-2024` using the default basis (
US 30/360):

    =YEARFRAC(DATE(2024, 1, 1), DATE(2024, 6, 30))

This formula will return `0.5` as the result because the period represents half of a 360-day year.

---

### Example 2: Using an Actual/Actual Basis

To calculate the fraction of the year between `01-Jan-2024` and `30-Jun-2024` using the actual/actual day count:

    =YEARFRAC(DATE(2024, 1, 1), DATE(2024, 6, 30), 1)

This formula will account for the actual number of days in the year (`2024` is a leap year) and will return
approximately `0.4959`.

---

### Example 3: Using the Actual/365 Basis

If you want to calculate the fraction of the year using a 365-day year:

    =YEARFRAC(DATE(2024, 1, 1), DATE(2024, 6, 30), 3)

This formula will return `0.4932`, as the period represents approximately 180 days out of 365.

---

### Example 4: Using European 30/360 Basis

To calculate the year fraction with the European 30/360 basis:

    =YEARFRAC(DATE(2024, 1, 1), DATE(2024, 6, 30), 4)

This formula will handle end-of-month scenarios differently compared to the US 30/360 convention and provide a result of
`0.5`.

## Notes

- `start_date` and `end_date` must be valid Excel dates. If not, the function will return a `#VALUE!` error.
- If `start_date` is later than `end_date`, the function will return a negative result.
- The result depends on the selected `basis`, so choose a value that matches your specific financial or project
  calculation needs.

The `YEARFRAC` function is versatile for time-based calculations, enabling precise proportional calculations across
various date ranges using different conventions.