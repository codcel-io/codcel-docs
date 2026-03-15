<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->


# WEEKDAY Function

The `WEEKDAY` function in Excel determines the day of the week for a given date, returning a numeric value corresponding to the day. It is highly useful for date analysis, scheduling, and applying conditional logic based on the day of the week.

## Syntax

```excel
WEEKDAY(date, [return_type])
```

- **`date`**: The date value for which you want to find the day of the week. This can be:
  - A date serial number.
  - A date string.
  - A result of other date functions like `DATE`.
- **`return_type`**: (Optional) A numeric argument that determines the numbering system for the days of the week. Values range from 1 to 17.

## Returns

The `WEEKDAY` function returns an integer representing the day of the week for the given date. The numbering system depends on the specified `return_type`.

---

## `return_type` Options and Behavior

| **Return Type** | **Weekday Numbering**                         | **Description**                             |
|------------------|----------------------------------------------|---------------------------------------------|
| `1` (Default)    | Sunday = 1, Monday = 2, ..., Saturday = 7    | Default behavior in Excel.                 |
| `2`              | Monday = 1, Tuesday = 2, ..., Sunday = 7     | Commonly used in ISO week conventions.     |
| `3`              | Monday = 0, Tuesday = 1, ..., Sunday = 6     | Used in programming and zero-based systems.|
| `11`             | Monday = 1, Tuesday = 2, ..., Sunday = 7     | Same as `2`.                               |
| `12`             | Tuesday = 1, Wednesday = 2, ..., Monday = 7  | Weeks start on Tuesday.                    |
| `13`             | Wednesday = 1, Thursday = 2, ..., Tuesday = 7| Weeks start on Wednesday.                  |
| `14`             | Thursday = 1, Friday = 2, ..., Wednesday = 7 | Weeks start on Thursday.                   |
| `15`             | Friday = 1, Saturday = 2, ..., Thursday = 7  | Weeks start on Friday.                     |
| `16`             | Saturday = 1, Sunday = 2, ..., Friday = 7    | Weeks start on Saturday.                   |
| `17`             | Sunday = 1, Monday = 2, ..., Saturday = 7    | Same as `1`.                               |

---

## Examples

### Example 1: Basic Usage
Suppose you want to find the day of the week for October 25, 2023:

```excel
=WEEKDAY(DATE(2023, 10, 25))
```

This formula calculates the weekday and returns `4` (Wednesday) using the default `return_type` (`1`).

### Example 2: Custom Week Start (Monday)
To use Monday as the start of the week:

```excel
=WEEKDAY(DATE(2023, 10, 25), 2)
```

This formula returns `3` (Wednesday) when Monday is `1`.

### Example 3: Week Start on Friday
To use Friday as the start of the week:

```excel
=WEEKDAY(DATE(2023, 10, 25), 15)
```

This formula returns `6` (Wednesday) when Friday is `1`.

---

## Key Features

1. **Flexible Day Numbering**: Supports multiple numbering conventions for international or cultural preferences.
2. **Customizable Week Start**: Allows selection of any day as the starting point of the week.
3. **Compatible with Other Functions**: Useful for conditional operations, trend analysis, and scheduling when combined with functions like `IF`, `CHOOSE`, or `TEXT`.

---

## Notes

- If `return_type` is omitted, it defaults to `1` (Sunday = 1, Saturday = 7).
- Ensure the `date` is a valid Excel date; otherwise, the function will return a `#VALUE!` error.
- `return_type` values not listed above will result in a `#VALUE!` error.

---

The `WEEKDAY` function in Excel is a robust tool for analyzing date-related data, offering unparalleled flexibility in numbering systems and starting days of the week. Use it to tailor date analyses to meet your specific needs.