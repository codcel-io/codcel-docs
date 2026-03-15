<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# EDATE Function

The `EDATE` function in Excel is used to calculate a date that is a specified number of months before or after a given
date. This function is commonly used for analyzing due dates, expiration dates, and other scenarios that require monthly
date offsets.

## Syntax

```plaintext
EDATE(start_date, months)
```

- **`start_date`**: The starting date. It must be a valid Excel date or a reference to a cell containing a date.
- **`months`**: The number of months to add (positive value) or subtract (negative value) from the `start_date`.

## Returns

The `EDATE` function returns a date that is the specified number of months before or after the given `start_date`. The
result is in Excel's date format, which can be displayed as a date or a serial number, depending on the cell's
formatting.

## Key Features

- **Dynamic Adjustments**: Accounts for varying month lengths, including leap years.
- **Supports Negative Values**: Easily calculate dates in the past by using negative `months`.
- **Error Handling**: Returns a `#VALUE!` error if the `start_date` is invalid or `months` is non-numeric.

## Example Usage

### Example 1: Adding Months

Suppose you have a starting date `2023-01-01` in cell `A1` and want to find the date three months later:

```plaintext
=EDATE(A1, 3)
```

This formula returns `2023-04-01` (3 months after January 1, 2023).

### Example 2: Subtracting Months

If you want to find the date five months before January 1, 2023:

```plaintext
=EDATE(A1, -5)
```

This formula returns `2022-08-01` (5 months before January 1, 2023).

### Example 3: Handling Leap Years

When calculating a date involving February in a leap year, Excel adjusts automatically. For example, starting from
`2024-01-31` and moving forward one month:

```plaintext
=EDATE(DATE(2024, 1, 31), 1)
```

This formula returns `2024-02-29`, correctly accounting for February 29 in the leap year 2024.

### Example 4: Dynamic Offsets

If the number of months is stored in cell `B1`, you can have a dynamic calculation like:

```plaintext
=EDATE(A1, B1)
```

This formula adjusts the date in `A1` based on the number of months specified in `B1`.

## Notes

- The `EDATE` function calculates based on the same day of the month as the `start_date`. If the result lands in a month
  with fewer days (e.g., starting on the 31st and moving to a month with 30 days), Excel adjusts the result to the last
  valid day of the resulting month.
- Dates should be formatted in Excel's date format for proper handling. Invalid dates will result in a `#VALUE!` error.
- Ensure the `months` argument is a numeric value. Non-numeric inputs will cause an error.

## Use Cases

- **Payment Schedules**: Calculate payment due dates by adding specific intervals to a start date.
- **Subscription Management**: Determine renewal dates for services or memberships.
- **Project Management**: Compute milestone deadlines by incrementing project start dates.
- **Warranty Tracking**: Determine expiration dates based on the product purchase date and warranty duration.

The `EDATE` function is a versatile tool in Excel that simplifies date calculations involving months, making it
essential for financial modeling, project planning, and scheduling tasks.