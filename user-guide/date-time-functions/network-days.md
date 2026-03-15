<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# NETWORKDAYS Function

The `NETWORKDAYS` function in Excel is used to calculate the number of whole working days between two dates. By default,
it excludes weekends (Saturday and Sunday) and can also exclude specified holidays. This function is particularly useful
when calculating project timelines or determining business days.

## Syntax

    NETWORKDAYS(start_date, end_date, [holidays])

- **`start_date`**: The start of the date range. This must be a valid Excel date.
- **`end_date`**: The end of the date range. This must also be a valid Excel date.
- **`[holidays]`** *(optional)*: A range of one or more dates to exclude from the working days calculation. This can be a
  cell range or an array of dates.

## Returns

The `NETWORKDAYS` function returns an integer representing the count of working days (Monday through Friday) between the
`start_date` and `end_date`. Weekends and any specified holidays are omitted from the count.

## Key Features

- **Business Day Calculation**: Ideal for determining the number of business days in a period, making it invaluable for
  project planning, payroll, and scheduling.
- **Customizable Holidays**: Allows exclusion of non-standard workdays (e.g., public holidays) for accurate working day
  calculations.
- **Simplicity**: Handles complex date range calculations with ease, saving time in manual calculations.

## Example Usage

### Example 1: Basic Usage

Suppose you want to calculate the number of working days between `01-Jan-2024` and `15-Jan-2024`.

    =NETWORKDAYS(DATE(2024, 1, 1), DATE(2024, 1, 15))

This formula will return `11`, excluding weekends.

---

### Example 2: Including Holidays

Now, suppose `01-Jan-2024` (New Year's Day) is a public holiday. You can specify it as a holiday to exclude.

    =NETWORKDAYS(DATE(2024, 1, 1), DATE(2024, 1, 15), {DATE(2024, 1, 1)})

This formula will return `10`, counting 11 working days minus 1 holiday.

---

### Example 3: Using a Cell Range for Holidays

If your holiday dates are listed in cells `A1:A3` (e.g., `01-Jan-2024`, `06-Jan-2024`, and `13-Jan-2024`), you can
reference them:

    =NETWORKDAYS(DATE(2024, 1, 1), DATE(2024, 1, 15), A1:A3)

This formula will subtract all holidays in the range `A1:A3` from the total working days.

---

### Example 4: Negative Result with Reversed Dates

If the `start_date` is after the `end_date`, the function returns a negative number:

    =NETWORKDAYS(DATE(2024, 1, 15), DATE(2024, 1, 1))

This formula will return `-11`, indicating 11 working days in the reversed direction.

## Notes

- The `start_date` and `end_date` automatically include both their respective working days in the count if they fall on
  weekdays.
- Ensure all date inputs are valid Excel dates to prevent errors.
- If the `start_date` is later than the `end_date`, the function will return a negative value based on the reversed
  order of dates.
- Public holidays can vary depending on a region or company policy; always update the `[holidays]` argument as per your
  requirements.
- The `NETWORKDAYS` function is available natively in Microsoft Excel. Codcel supports `NETWORKDAYS` directly with the
  same syntax and behavior.
- Use the `NETWORKDAYS.INTL` function for custom weekend definitions beyond the default Saturday-Sunday.
- Related functions include `WORKDAY` (returns a date a given number of working days before or after a start date) and
  `DAYS` (returns the total number of days between two dates without excluding weekends or holidays).

## Use Cases

- **Project Planning**: Calculate the number of business days available for completing a project between two milestones.
- **Payroll Processing**: Determine the number of working days in a pay period to calculate wages or salaries.
- **Scheduling and Deadlines**: Compute how many working days remain until a deadline, accounting for weekends and
  holidays.
- **Service Level Agreements (SLAs)**: Track working-day-based response or resolution times for customer support or
  contracts.

The `NETWORKDAYS` function is a powerful tool to calculate the effective number of working days within any time frame,
simplifying time-sensitive business operations and project management.