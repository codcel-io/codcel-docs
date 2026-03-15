<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# WORKDAY Function

The `WORKDAY` function in Excel is used to calculate the date of a working day that is a specified number of working
days before or after a start date. By default, it excludes weekends (Saturday and Sunday) and can also exclude any
specified holidays. This function is helpful for project management and date-based scheduling tasks.

## Syntax

    WORKDAY(start_date, days, [holidays])

- `start_date`: A valid Excel date representing the starting point for the calculation.
- `days`: The number of working days to add (positive) or subtract (negative) from `start_date`.
- `[holidays]` *(optional)*: An optional range or array of dates representing non-standard workdays (e.g., public
  holidays) to exclude.

## Returns

The `WORKDAY` function returns a date that is the calculated working day, adjusted to exclude weekends and any specified
holidays.

## Key Features

- **Date Projection**: Useful for calculating future or past business days from a given date, helping in planning
  deadlines or setting completion dates.
- **Customizable Holidays**: Allows you to exclude additional dates (e.g., public holidays) beyond the standard weekends
  for an accurate calculation.

## Example

### Example 1: Basic Usage

Suppose you want to calculate the date 10 working days after `01-Jan-2024`.

    =WORKDAY(DATE(2024, 1, 1), 10)

This formula will return `15-Jan-2024`, skipping weekends.

---

### Example 2: Including Holidays

Now, suppose `01-Jan-2024` (New Year's Day) is a public holiday. You can specify it as a holiday in the `WORKDAY`
function.

    =WORKDAY(DATE(2024, 1, 1), 10, {DATE(2024, 1, 1)})

This formula will return `16-Jan-2024`, adjusting for the holiday in addition to the weekends.

---

### Example 3: Using a Cell Range for Holidays

If holiday dates (e.g., `01-Jan-2024`, `06-Jan-2024`, and `13-Jan-2024`) are listed in cells `A1:A3`, you can reference
them:

    =WORKDAY(DATE(2024, 1, 1), 10, A1:A3)

This formula will account for all holidays in the range `A1:A3` and adjust the result accordingly.

---

### Example 4: Calculating with Negative Days

To calculate 10 working days before `15-Jan-2024`:

    =WORKDAY(DATE(2024, 1, 15), -10)

This formula will return `01-Jan-2024`, skipping weekends.

## Notes

- The `start_date` is counted only if it falls on a working day. Otherwise, the calculation begins from the next working
  day.
- Dates provided for the `holidays` parameter must be valid Excel dates.
- If the resulting date is adjusted into a weekend or holiday, the function will skip over it to the nearest working
  day.
- Use the `WORKDAY.INTL` function for custom weekend definitions beyond the default Saturday-Sunday.

The `WORKDAY` function is an essential tool for planning and scheduling work projects, enabling you to calculate
deadlines and milestones accurately while accounting for non-working days.