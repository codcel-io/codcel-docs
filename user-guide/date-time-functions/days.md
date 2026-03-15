<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DAYS Function

The `DAYS` function in Excel is used to calculate the number of days between two dates. It is particularly useful
for performing date-based calculations, such as determining durations or time intervals.

## Syntax

```plaintext
DAYS(end_date, start_date)
```

- `end_date`: This is the later date in the range you are calculating. It must be in a valid Excel date format or
  referenced as a cell containing such a date.
- `start_date`: This is the earlier date in the range you are calculating. It must also be in a valid Excel date
  format or referenced as a cell containing such a date.

## Returns

The `DAYS` function returns an integer value representing the number of days between the `end_date` and `start_date`.
The result can be positive, negative, or zero depending on the relative positioning of the two dates.

## Key Features

- **Date Interval Calculation**: Provides a quick and easy way to determine the number of days between two dates.
- **Supports Direct and Referenced Dates**: Works with both cell references and directly input date values.
- **Handles Negative Values**: Returns a negative number if the `start_date` is after the `end_date`.

## Example

Suppose you have two dates in cells `A1` (`2023-01-01`) and `A2` (`2023-12-31`).

```plaintext
=DAYS(A2, A1)
```

This formula returns `364`, as there are 364 days between January 1, 2023, and December 31, 2023.

For direct date values without cell references:

```plaintext
=DAYS(DATE(2023, 12, 31), DATE(2023, 1, 1))
```

This formula also returns `364`, representing the same number of days between January 1, 2023, and December 31, 2023.

## Notes

- Ensure that both `start_date` and `end_date` are in a valid date format recognized by Excel to avoid errors.
- If either of the dates is invalid or text that cannot be interpreted as a date, Excel will return a `#VALUE!` error.
- Leap years are taken into account when calculating durations with this function.

## Use Cases

- **Project Duration Calculation**: Determine the number of days between the start and end dates of a project.
- **Event Planning**: Compute the time remaining until a future event or the time elapsed since a past one.
- **Financial Analysis**: Calculate durations for loan terms, investments, or payment cycles.

The `DAYS` function is a simple yet powerful tool for managing time intervals and performing precise date-based
calculations in Excel.