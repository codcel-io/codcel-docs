<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# WORKDAY.INTL Function

The `WORKDAY.INTL` function in Excel is used to calculate the date of a working day that is a specified number of working
days before or after a start date, with the ability to specify which days of the week are considered weekends. Unlike
`WORKDAY`, which always treats Saturday and Sunday as weekends, `WORKDAY.INTL` lets you define custom weekend days to
accommodate different regional or business schedules. It can also exclude specified holidays from the calculation.

## Syntax

    WORKDAY.INTL(start_date, days, [weekend], [holidays])

- **`start_date`**: A valid Excel date representing the starting point for the calculation.
- **`days`**: The number of working days to add (positive) or subtract (negative) from `start_date`.
- **`[weekend]`** *(optional)*: A number or string that specifies which days of the week are weekend (non-working) days.
  Defaults to `1` (Saturday and Sunday). See the Weekend Values table below.
- **`[holidays]`** *(optional)*: A range of one or more dates representing non-standard workdays (e.g., public holidays)
  to exclude. This can be a cell range or an array of dates.

### Weekend Values

The `weekend` parameter accepts either a number code or a seven-character string:

#### Number Codes

| Value | Weekend Days          |
|-------|-----------------------|
| 1     | Saturday, Sunday      |
| 2     | Sunday, Monday        |
| 3     | Monday, Tuesday       |
| 4     | Tuesday, Wednesday    |
| 5     | Wednesday, Thursday   |
| 6     | Thursday, Friday      |
| 7     | Friday, Saturday      |
| 11    | Sunday only           |
| 12    | Monday only           |
| 13    | Tuesday only          |
| 14    | Wednesday only        |
| 15    | Thursday only         |
| 16    | Friday only           |
| 17    | Saturday only         |

#### Seven-Character String

You can also pass a 7-character string of `0`s and `1`s, where each character represents a day of the week starting with
Monday. A `1` indicates a weekend (non-working) day and a `0` indicates a working day.

| Position | Day       |
|----------|-----------|
| 1        | Monday    |
| 2        | Tuesday   |
| 3        | Wednesday |
| 4        | Thursday  |
| 5        | Friday    |
| 6        | Saturday  |
| 7        | Sunday    |

For example, `"0000011"` means Saturday and Sunday are weekends (the default), while `"1000001"` means Monday and Sunday
are weekends.

## Returns

The `WORKDAY.INTL` function returns a date that is the calculated working day, adjusted to exclude the specified weekend
days and any listed holidays.

## Key Features

- **Custom Weekend Definitions**: Unlike `WORKDAY`, you can define any combination of days as weekends using number codes
  or a 7-character string, making it suitable for regions or industries with non-standard work weeks.
- **Date Projection**: Useful for calculating future or past business days from a given date, helping in planning
  deadlines or setting completion dates across different work-week configurations.
- **Flexible Holiday Exclusion**: Allows exclusion of non-standard workdays (e.g., public holidays) for accurate date
  calculations.

## Example Usage

### Example 1: Basic Usage (Default Weekends)

Suppose you want to calculate the date 10 working days after `01-Jan-2024` using the default Saturday–Sunday weekend.

    =WORKDAY.INTL(DATE(2024, 1, 1), 10)

This formula will return `15-Jan-2024`, the same result as `WORKDAY` since the default weekend is Saturday and Sunday.

---

### Example 2: Friday–Saturday Weekend

In many Middle Eastern countries, the weekend is Friday and Saturday. To calculate 10 working days after `01-Jan-2024`
with this schedule:

    =WORKDAY.INTL(DATE(2024, 1, 1), 10, 7)

This formula will return `15-Jan-2024`, skipping Fridays and Saturdays instead of Saturdays and Sundays.

---

### Example 3: Sunday-Only Weekend

If only Sunday is a non-working day, use weekend code `11`:

    =WORKDAY.INTL(DATE(2024, 1, 1), 10, 11)

This formula will return `12-Jan-2024`, since only Sundays are excluded from the count.

---

### Example 4: Using a Weekend String

To specify that Wednesday and Sunday are the weekend days, use the 7-character string `"0010001"`:

    =WORKDAY.INTL(DATE(2024, 1, 1), 10, "0010001")

This formula will return `15-Jan-2024`, skipping every Wednesday and Sunday in the calculation.

---

### Example 5: Custom Weekend with Holidays

Suppose the weekend is Friday and Saturday (code `7`), and `01-Jan-2024` (New Year's Day) is a public holiday:

    =WORKDAY.INTL(DATE(2024, 1, 1), 10, 7, {DATE(2024, 1, 1)})

This formula will return `16-Jan-2024`, adjusting for the holiday in addition to the custom weekend days.

---

### Example 6: Using a Cell Range for Holidays

If holiday dates (e.g., `01-Jan-2024`, `06-Jan-2024`, and `13-Jan-2024`) are listed in cells `A1:A3`, with a
Sunday-only weekend:

    =WORKDAY.INTL(DATE(2024, 1, 1), 10, 11, A1:A3)

This formula will account for all holidays in the range `A1:A3` and adjust the result accordingly.

---

### Example 7: Calculating with Negative Days

To calculate 10 working days before `15-Jan-2024` with a Friday–Saturday weekend (code `7`):

    =WORKDAY.INTL(DATE(2024, 1, 15), -10, 7)

This formula will return `01-Jan-2024`, counting backwards and skipping Fridays and Saturdays.

## Notes

- The `start_date` is counted only if it falls on a working day. Otherwise, the calculation begins from the next working
  day.
- Dates provided for the `holidays` parameter must be valid Excel dates.
- If the resulting date is adjusted into a weekend or holiday, the function will skip over it to the nearest working day.
- A `weekend` string of all `1`s (`"1111111"`) is invalid because it would mean every day is a weekend, leaving no
  working days. This will return a `#VALUE!` error.
- Public holidays can vary depending on a region or company policy; always update the `[holidays]` argument as per your
  requirements.
- The `WORKDAY.INTL` function is available natively in Microsoft Excel. Codcel supports `WORKDAY.INTL` directly with the
  same syntax and behavior.
- Use the standard `WORKDAY` function if you only need the default Saturday–Sunday weekend schedule.
- Related functions include `NETWORKDAYS.INTL` (calculates the number of working days between two dates, with custom
  weekends), `NETWORKDAYS` (same as `NETWORKDAYS.INTL` but with fixed Saturday–Sunday weekends), and `DAYS` (returns the
  total number of days between two dates without excluding weekends or holidays).

## Use Cases

- **International Project Planning**: Calculate deadline dates for projects across regions with different work-week
  structures (e.g., Sunday–Thursday in the Middle East, Monday–Friday in the West).
- **Payroll Processing**: Determine pay dates or due dates for employees with non-standard work schedules, such as those
  who work Tuesday through Saturday.
- **Shift-Based Scheduling**: Compute target dates for industries like healthcare or manufacturing where weekends may
  differ from the traditional Saturday–Sunday model.
- **Service Level Agreements (SLAs)**: Calculate working-day-based response or resolution deadlines for customer support
  or contracts, accounting for regional weekend differences.

The `WORKDAY.INTL` function is a versatile tool for calculating target working dates across any work-week configuration,
simplifying deadline and milestone planning in a globalized environment.