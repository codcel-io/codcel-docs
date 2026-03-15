<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Date and Time Functions

This contains the list of date and time functions that are currently supported by Codcel.

## Basic Date Functions

### [`DATE`](date-time-functions/date.md)
Creates a date from year, month, and day.

- **Example:** `=DATE(2023, 12, 31)`

### [`DATEDIF`](date-time-functions/date_dif.md)
Calculates the difference between two dates in years, months, or days.

- **Example:** `=DATEDIF(A1, B1, "Y")`

### [DATEVALUE](./date-time-functions/date-value.md)
Converts a date in text format into an actual date value that Excel recognizes.

- **Purpose:** Parses a date represented as a text string and converts it into a date value that Excel can use for
  calculations or formatting. This is useful when working with dates stored as text.

- **Formula:** `DATEVALUE(date_text)`
    - `date_text` is a string representing a date in an acceptable format. It must be a valid date or reference to a cell
      containing a valid text-formatted date.

- **Example Usage:**
    - `=DATEVALUE("01-Jan-2022")` returns the corresponding date value (serial number) for January 1, 2022.
    - `=DATEVALUE("2022/01/01")` also returns the date value for January 1, 2022.
    - `=DATEVALUE(A1)` converts a text date in the cell `A1` into a date value.

### [`DAYS`](date-time-functions/days.md)
Returns the number of days between two dates.

- **Purpose:** Calculates the difference in the number of days between two dates.

- **Formula:** `DAYS(end_date, start_date)`
  - `end_date` is the later date.
  - `start_date` is the earlier date.

- **Example Usage:**
  - `=DAYS("2023-12-31", "2023-01-01")` returns `364`.
  - `=DAYS(A1, A2)` calculates the difference between the dates in cells `A1` and `A2`.

### [`DAYS360`](date-time-functions/days-360.md)
Returns the number of days between two dates based on a 360-day year (12 months of 30 days).

- **Purpose:** Useful for financial calculations where a standardized 360-day calendar is used.

- **Formula:** `DAYS360(start_date, end_date, [method])`
  - `start_date` is the starting date.
  - `end_date` is the ending date.
  - `[method]` is an optional argument:
    - If `FALSE` or omitted: Uses the U.S. (NASD) method, which adjusts for month-end differences.
    - If `TRUE`: Uses the European method, which assumes all months have 30 days, even February.

- **Example Usage:**
  - `=DAYS360("2023-01-01", "2023-12-31")` returns the number of days based on a 360-day year.
  - `=DAYS360(A1, A2, TRUE)` calculates the difference between the dates in cells `A1` and `A2` using the European
    method.

## E

### [`EDATE`](./date-time-functions/e-date.md)
Returns the date that is a specified number of months before or after a start date.

- **Purpose:** Calculates a date that is a specified number of months before (negative value) or after (positive value)
  the given start date.

- **Formula:** `EDATE(start_date, months)`
  - `start_date` is the initial date from which to calculate.
  - `months` is the number of months to offset. It can be positive or negative.

- **Example Usage:**
  - `=EDATE("2023-01-01", 6)` returns `2023-07-01` (6 months after January 1, 2023).
  - `=EDATE("2023-01-01", -6)` returns `2022-07-01` (6 months before January 1, 2023).
  - `=EDATE(A1, 12)` adds one year (12 months) to the date in cell `A1`.

### [`EOMONTH`](date-time-functions/eo-month.md)
Returns the last day of the month, offset by a number of months.

- **Purpose:** Calculates the last day of the month that is a specified number of months before or after a given start
  date.

- **Formula:** `EOMONTH(start_date, months)`
  - `start_date` is the starting date from which the calculation begins.
  - `months` is the number of months to offset. It can be positive (future months) or negative (past months).

- **Example Usage:**
  - `=EOMONTH("2023-01-01", 1)` returns `2023-02-28` (last day of February 2023).
  - `=EOMONTH("2023-01-01", -1)` returns `2022-12-31` (last day of December 2022).
  - `=EOMONTH(A1, 12)` calculates the last day of the month, 12 months (1 year) after the date in cell `A1`.

## Current Date and Time

### [`TIMEVALUE`](date-time-functions/time-value.md)
Converts a time in text format into an Excel time value.

- **Purpose:** Parses a time represented as a text string and converts it into a time value that Excel recognizes. This
  is helpful when working with times stored as text.

- **Formula:** `TIMEVALUE(time_text)`
  - `time_text` is a string representing a time in an acceptable format. It must be a valid time or reference to a cell
    containing a valid text-formatted time.

- **Example Usage:**
  - `=TIMEVALUE("2:00 PM")` returns the corresponding time value for 2:00 PM.
  - `=TIMEVALUE("14:30")` returns the time value for 2:30 PM.
  - `=TIMEVALUE(A1)` converts a text time in the cell `A1` into a time value.

### [`TODAY`](date-time-functions/today.md)
Returns the current date without the time.

- **Example:** `=TODAY()`

## N

### [`NETWORKDAYS`](date-time-functions/network-days.md)
Calculates the number of workdays (Monday through Friday) between two dates, excluding weekends and optionally specified
holidays.

- **Purpose:** Helps calculate the number of working days within a date range, making it ideal for project planning
  while excluding weekends and holidays.

- **Formula:** `NETWORKDAYS(start_date, end_date, [holidays])`
  - `start_date` is the initial date of the range.
  - `end_date` is the final date of the range.
  - `[holidays]` is an optional argument for specifying a range of dates to exclude (e.g., public holidays).

- **Example Usage:**
  - `=NETWORKDAYS("2023-01-01", "2023-01-31")` returns `23` (January 2023 includes 23 weekdays).
  - `=NETWORKDAYS("2023-01-01", "2023-01-31", {"2023-01-16", "2023-01-26"})` returns `21` (23 weekdays minus 2
    holidays).
  - `=NETWORKDAYS(A1, A2, B1:B5)` calculates the number of working days between the dates in cells `A1` and `A2`,
    excluding holidays listed in the range `B1:B5`.

### [`NOW`](date-time-functions/now.md)
Returns the current date and time.

- **Example:** `=NOW()`

## Day, Month, Year Functions

### [`DAY`](date-time-functions/day.md)
Extracts the day from a date.

- **Example:** `=DAY(A1)`

### [`MONTH`](date-time-functions/month.md)
Extracts the month from a date.

- **Example:** `=MONTH(A1)`

### [`YEAR`](date-time-functions/year.md)
Extracts the year from a date.

- **Example:** `=YEAR(A1)`

## W

### [`WORKDAY`](date-time-functions/work-day.md)  
Returns a date that is a given number of workdays before or after the start date, excluding weekends and optionally
specified holidays.

- **Purpose:** Calculates a workday date by adding or subtracting a specified number of workdays from a start date.
  Ideal for scheduling tasks, accounting for weekends and holidays.

- **Formula:** `WORKDAY(start_date, days, [holidays])`
  - `start_date` is the initial date from which the calculation begins.
  - `days` is the number of workdays to offset.
    - Use a positive number to calculate a future date.
    - Use a negative number to calculate a past date.
  - `[holidays]` is an optional argument for specifying a range of dates to exclude (e.g., public holidays).

- **Example Usage:**
  - `=WORKDAY("2023-01-01", 10)` returns the date 10 workdays after January 1, 2023.
  - `=WORKDAY("2023-01-01", -5)` returns the date 5 workdays before January 1, 2023.
  - `=WORKDAY(A1, 20, B1:B10)` calculates the date 20 workdays after the date in cell `A1`, excluding holidays listed in
    the range `B1:B10`.

### [`WEEKDAY`](date-time-functions/week_day.md)
Returns the day of the week as a number.

- **Example:** `=WEEKDAY(A1)`

### [`WEEKNUM`](date-time-functions/week_num.md)
Returns the week number of the year for a given date.

- **Example:** `=WEEKNUM(A1)`

### [`ISOWEEKNUM`](date-time-functions/iso_week_num.md)
Returns the ISO week number of the year.

- **Example:** `=ISOWEEKNUM(A1)`

## Time Functions

### [`TIME`](date-time-functions/time.md)
Creates a time from hours, minutes, and seconds.

- **Example:** `=TIME(7, 12, 31)`

### [`HOUR`](date-time-functions/hour.md)
Extracts the hour from a time.

- **Example:** `=HOUR(A1)`

### [`MINUTE`](date-time-functions/minute.md)
Extracts the minute from a time.

- **Example:** `=MINUTE(A1)`

### [`SECOND`](date-time-functions/second.md)
Extracts the second from a time.

- **Example:** `=SECOND(A1)`

### `TIMEVALUE`
Converts a time in text format into an Excel time value.

- **Example:** `=TIMEVALUE("2:00 PM")`

## Advanced Date Functions

### `EOMONTH`
Returns the last day of the month, offset by a number of months.

### `EDATE`
Returns the date that is a specified number of months before or after a start date.

### [`NETWORKDAYS.INTL`](date-time-functions/network-days-intl.md)
Calculates the number of workdays between two dates, with the ability to specify custom weekend days and optionally
exclude holidays. Extends `NETWORKDAYS` for non-standard work-week configurations.

- **Purpose:** Helps calculate the number of working days within a date range using custom weekend definitions, making it
  ideal for international or shift-based project planning.

- **Formula:** `NETWORKDAYS.INTL(start_date, end_date, [weekend], [holidays])`
  - `start_date` is the initial date of the range.
  - `end_date` is the final date of the range.
  - `[weekend]` is an optional number code or 7-character string specifying which days are weekends. Defaults to `1`
    (Saturday and Sunday).
  - `[holidays]` is an optional argument for specifying a range of dates to exclude (e.g., public holidays).

- **Example Usage:**
  - `=NETWORKDAYS.INTL("2024-01-01", "2024-01-15")` returns `11` (default Saturday–Sunday weekend).
  - `=NETWORKDAYS.INTL("2024-01-01", "2024-01-15", 7)` returns `11` (Friday–Saturday weekend).
  - `=NETWORKDAYS.INTL("2024-01-01", "2024-01-15", 11)` returns `13` (Sunday-only weekend).
  - `=NETWORKDAYS.INTL(A1, A2, "0010001", B1:B5)` calculates working days with Wednesday and Sunday as weekends,
    excluding holidays in `B1:B5`.

### `WORKDAY`
Returns the date after a specified number of workdays.

### [`WORKDAY.INTL`](date-time-functions/workday-intl.md)
Returns a date that is a given number of workdays before or after the start date, with the ability to specify custom
weekend days and optionally exclude holidays. Extends `WORKDAY` for non-standard work-week configurations.

- **Purpose:** Calculates a workday date by adding or subtracting a specified number of workdays from a start date using
  custom weekend definitions, making it ideal for international or shift-based scheduling.

- **Formula:** `WORKDAY.INTL(start_date, days, [weekend], [holidays])`
  - `start_date` is the initial date from which the calculation begins.
  - `days` is the number of workdays to offset.
    - Use a positive number to calculate a future date.
    - Use a negative number to calculate a past date.
  - `[weekend]` is an optional number code or 7-character string specifying which days are weekends. Defaults to `1`
    (Saturday and Sunday).
  - `[holidays]` is an optional argument for specifying a range of dates to exclude (e.g., public holidays).

- **Example Usage:**
  - `=WORKDAY.INTL("2024-01-01", 10)` returns the date 10 workdays after January 1, 2024 (default Saturday–Sunday
    weekend).
  - `=WORKDAY.INTL("2024-01-01", 10, 7)` returns the date 10 workdays after January 1, 2024 (Friday–Saturday weekend).
  - `=WORKDAY.INTL("2024-01-01", 10, 11)` returns the date 10 workdays after January 1, 2024 (Sunday-only weekend).
  - `=WORKDAY.INTL(A1, 20, "0010001", B1:B10)` calculates the date 20 workdays after the date in cell `A1` with
    Wednesday and Sunday as weekends, excluding holidays in `B1:B10`.

## Text Conversion and Formatting

### `TEXT`
Converts a date to a specified format.

## Miscellaneous

### `SEQUENCE`
Generates a sequence of dates.

### [`YEARFRAC`](date-time-functions/year-frac.md)
Calculates the fraction of the year represented by the number of whole days between two dates.

- **Purpose:** Helps determine the proportion of a year between two dates, often used in financial calculations such as
  interest accrual.

- **Formula:** `YEARFRAC(start_date, end_date, [basis])`
  - `start_date` is the starting date for the calculation.
  - `end_date` is the ending date for the calculation.
  - `[basis]` is an optional argument specifying the day count basis to use. Default is `0` (30/360 US).
    - `0` or omitted: US (NASD) 30/360.
    - `1`: Actual/actual.
    - `2`: Actual/360.
    - `3`: Actual/365.
    - `4`: European 30/360.

- **Example Usage:**
  - `=YEARFRAC("2023-01-01", "2023-12-31")` returns `1` (the entire year).
  - `=YEARFRAC("2023-01-01", "2023-06-30")` returns `0.5` (half a year).
  - `=YEARFRAC("2023-01-01", "2024-01-01", 1)` calculates the fraction of the year between the two dates using an
    actual/actual day count basis.