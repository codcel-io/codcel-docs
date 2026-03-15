<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# NETWORKDAYS.INTL Function

The `NETWORKDAYS.INTL` function in Excel is used to calculate the number of whole working days between two dates, with
the ability to specify which days of the week are considered weekends. Unlike `NETWORKDAYS`, which always treats Saturday
and Sunday as weekends, `NETWORKDAYS.INTL` lets you define custom weekend days to accommodate different regional or
business schedules. It can also exclude specified holidays from the count.

## Syntax

    NETWORKDAYS.INTL(start_date, end_date, [weekend], [holidays])

- **`start_date`**: The start of the date range. This must be a valid Excel date.
- **`end_date`**: The end of the date range. This must also be a valid Excel date.
- **`[weekend]`** *(optional)*: A number or string that specifies which days of the week are weekend (non-working) days.
  Defaults to `1` (Saturday and Sunday). See the Weekend Values table below.
- **`[holidays]`** *(optional)*: A range of one or more dates to exclude from the working days calculation. This can be
  a cell range or an array of dates.

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

The `NETWORKDAYS.INTL` function returns an integer representing the count of working days between the `start_date` and
`end_date`, excluding the specified weekend days and any listed holidays.

## Key Features

- **Custom Weekend Definitions**: Unlike `NETWORKDAYS`, you can define any combination of days as weekends using number
  codes or a 7-character string, making it suitable for regions or industries with non-standard work weeks.
- **Flexible Holiday Exclusion**: Allows exclusion of non-standard workdays (e.g., public holidays) for accurate working
  day calculations.
- **Business Day Calculation**: Ideal for determining the number of business days in a period, making it invaluable for
  project planning, payroll, and scheduling across different work-week configurations.

## Example Usage

### Example 1: Basic Usage (Default Weekends)

Suppose you want to calculate the number of working days between `01-Jan-2024` and `15-Jan-2024` using the default
Saturday–Sunday weekend.

    =NETWORKDAYS.INTL(DATE(2024, 1, 1), DATE(2024, 1, 15))

This formula will return `11`, the same result as `NETWORKDAYS` since the default weekend is Saturday and Sunday.

---

### Example 2: Friday–Saturday Weekend

In many Middle Eastern countries, the weekend is Friday and Saturday. To calculate working days with this schedule:

    =NETWORKDAYS.INTL(DATE(2024, 1, 1), DATE(2024, 1, 15), 7)

This formula will return `11`, excluding Fridays and Saturdays instead of Saturdays and Sundays.

---

### Example 3: Sunday-Only Weekend

If only Sunday is a non-working day, use weekend code `11`:

    =NETWORKDAYS.INTL(DATE(2024, 1, 1), DATE(2024, 1, 15), 11)

This formula will return `13`, since only Sundays are excluded from the 15-day range.

---

### Example 4: Using a Weekend String

To specify that Wednesday and Sunday are the weekend days, use the 7-character string `"0010001"`:

    =NETWORKDAYS.INTL(DATE(2024, 1, 1), DATE(2024, 1, 15), "0010001")

This formula will return `11`, excluding every Wednesday and Sunday in the date range.

---

### Example 5: Custom Weekend with Holidays

Suppose the weekend is Friday and Saturday (code `7`), and `01-Jan-2024` (New Year's Day) is a public holiday:

    =NETWORKDAYS.INTL(DATE(2024, 1, 1), DATE(2024, 1, 15), 7, {DATE(2024, 1, 1)})

This formula will return `10`, counting 11 working days minus 1 holiday.

---

### Example 6: Using a Cell Range for Holidays

If your holiday dates are listed in cells `A1:A3` (e.g., `01-Jan-2024`, `06-Jan-2024`, and `13-Jan-2024`), with a
Sunday-only weekend:

    =NETWORKDAYS.INTL(DATE(2024, 1, 1), DATE(2024, 1, 15), 11, A1:A3)

This formula will subtract all holidays in the range `A1:A3` from the total working days.

---

### Example 7: Negative Result with Reversed Dates

If the `start_date` is after the `end_date`, the function returns a negative number:

    =NETWORKDAYS.INTL(DATE(2024, 1, 15), DATE(2024, 1, 1), 1)

This formula will return `-11`, indicating 11 working days in the reversed direction.

## Notes

- The `start_date` and `end_date` automatically include both their respective working days in the count if they fall on
  working days.
- Ensure all date inputs are valid Excel dates to prevent errors.
- If the `start_date` is later than the `end_date`, the function will return a negative value based on the reversed
  order of dates.
- A `weekend` string of all `1`s (`"1111111"`) is invalid because it would mean every day is a weekend, leaving no
  working days. This will return a `#VALUE!` error.
- Public holidays can vary depending on a region or company policy; always update the `[holidays]` argument as per your
  requirements.
- The `NETWORKDAYS.INTL` function is available natively in Microsoft Excel. Codcel supports `NETWORKDAYS.INTL` directly
  with the same syntax and behavior.
- Use the standard `NETWORKDAYS` function if you only need the default Saturday–Sunday weekend schedule.
- Related functions include `WORKDAY.INTL` (returns a date a given number of working days before or after a start date,
  with custom weekends), `WORKDAY` (same as `WORKDAY.INTL` but with fixed Saturday–Sunday weekends), and `DAYS`
  (returns the total number of days between two dates without excluding weekends or holidays).

## Use Cases

- **International Project Planning**: Calculate the number of business days available for completing a project across
  regions with different work-week structures (e.g., Sunday–Thursday in the Middle East, Monday–Friday in the West).
- **Payroll Processing**: Determine the number of working days in a pay period for employees with non-standard work
  schedules, such as those who work Tuesday through Saturday.
- **Shift-Based Scheduling**: Compute working days for industries like healthcare or manufacturing where weekends may
  differ from the traditional Saturday–Sunday model.
- **Service Level Agreements (SLAs)**: Track working-day-based response or resolution times for customer support or
  contracts, accounting for regional weekend differences.

The `NETWORKDAYS.INTL` function is a versatile tool for calculating effective working days within any time frame and
across any work-week configuration, simplifying time-sensitive business operations in a globalized environment.