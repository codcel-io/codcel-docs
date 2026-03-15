<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->


# WEEKNUM Function

The `WEEKNUM` function in Excel is used to determine the week number of the year for a given date. It plays a crucial role in date analysis, especially in scenarios where week-based analysis or reporting is required.

## Syntax

```excel
WEEKNUM(date, [return_type])
```

- **`date`**: A date value for which you want to find the week number. This can be:
  - A date serial number.
  - A text date.
  - A result from other date functions like `DATE`.
- **`return_type`**: (Optional) A numeric argument that determines the type of the week numbering system to use. Values range from 1 to 21.

## Returns

The `WEEKNUM` function returns an integer representing the week number for the supplied date in the year. The numbering system depends on the specified `return_type`.

---

## `return_type` Options and Behavior

| **Return Type** | **Week Start Day**  | **Description**                             |
|------------------|---------------------|---------------------------------------------|
| `1` (Default)    | Sunday              | Weeks start on Sunday.                     |
| `2`              | Monday              | ISO 8601 standard, weeks start on Monday.  |
| `11`             | Monday              | Weeks start on Monday.                     |
| `12`             | Tuesday             | Weeks start on Tuesday.                    |
| `13`             | Wednesday           | Weeks start on Wednesday.                  |
| `14`             | Thursday            | Weeks start on Thursday.                   |
| `15`             | Friday              | Weeks start on Friday.                     |
| `16`             | Saturday            | Weeks start on Saturday.                   |
| `17`             | Sunday              | Weeks start on Sunday.                     |
| `21`             | Monday              | ISO standard with weeks starting on Monday.|

---

## Examples

### Example 1: Basic Usage
Suppose you want to find the week number of the year for October 25, 2023:

```excel
=WEEKNUM(DATE(2023, 10, 25))
```

This formula calculates the week number and returns `43` (assuming the default `return_type` of `1`, where weeks start on Sunday).

### Example 2: Custom Week Start (Monday)
To use Monday as the start of the week:

```excel
=WEEKNUM(DATE(2023, 10, 25), 2)
```

This formula may return `44`, representing the week number when weeks start on Monday.

### Example 3: Week Start on Friday
To use Friday as the start of the week:

```excel
=WEEKNUM(DATE(2023, 10, 25), 15)
```

This formula may return `43`, representing the week number when weeks start on Friday.

---

## Key Features

1. **Week Number Calculation**: Efficiently calculates the week number for any specified date.
2. **Customizable Starting Day**: Allows adjustment of the starting day of the week, aligning with international or organizational standards.
3. **Flexible Integration**: Works seamlessly with other Excel functions like `DATE`, `TEXT`, and `IF`.

---

## Notes

- If `return_type` is omitted, it defaults to `1` (weeks start on Sunday).
- The `date` must be a valid Excel date; otherwise, the function will return a `#VALUE!` error.
- Values for `return_type` not listed above will result in a `#VALUE!` error.

---

The `WEEKNUM` function in Excel is a powerful tool for determining the week of the year for any given date. It is particularly valuable for weekly reporting, scheduling, and trend analysis, supporting various conventions and standards to fit diverse needs.