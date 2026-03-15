<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# EOMONTH Function

The `EOMONTH` function in Excel is used to calculate the last day of a month that is a given number of months before or
after the specified start date. This function is particularly useful for financial and scheduling applications, where
end-of-month dates are needed.

## Syntax

```plaintext
EOMONTH(start_date, months)
```

- **`start_date`**: The starting date. It must be a valid Excel date or a reference to a cell containing a date.
- **`months`**: The number of months to add (positive value) or subtract (negative value) from the `start_date`.

## Returns

The `EOMONTH` function returns the last day of the month that is the specified number of months before or after the
given `start_date`. The result is in Excel's date format, which can be displayed as a date or as a serial number,
depending on the cell's formatting.

## Key Features

- **End-of-Month Precision**: Always returns the last day of the specified month, regardless of its length or leap year.
- **Supports Negative Values**: Easily calculate past end-of-month dates using negative `months` values.
- **Error Handling**: Returns a `#VALUE!` error if the `start_date` is invalid or the `months` argument is non-numeric.

## Example Usage

### Example 1: Adding Months

Suppose you have a starting date `2023-01-15` in cell `A1` and want to find the last day of the month three months
later:

```plaintext
=EOMONTH(A1, 3)
```

This formula returns `2023-04-30`, the last day of April 2023, three months after January 2023.

### Example 2: Subtracting Months

To find the last day of the month five months before January 2023:

```plaintext
=EOMONTH(A1, -5)
```

This formula returns `2022-08-31`, the last day of August 2022, five months prior to January 2023.

### Example 3: Leap Year Handling

The `EOMONTH` function correctly accounts for leap years. For example, starting from `2024-01-15` and moving forward two
months:

```plaintext
=EOMONTH(DATE(2024, 1, 15), 2)
```

This formula returns `2024-03-31`, the last day of March 2024, which follows the leap year February.

### Example 4: Dynamic Offsets

If the number of months is stored dynamically in cell `B1`, you can use the formula:

```plaintext
=EOMONTH(A1, B1)
```

This formula adjusts the `start_date` in `A1` based on the number of months specified in `B1`.

## Notes

- The `EOMONTH` function is often used in financial models for period-ending calculations.
- Returns the last day of the resulting month, even if the `start_date` is not the first or last day of the original
  month.
- Ensure that both the `start_date` and `months` arguments are valid to avoid errors.
- The function works with both Excel’s normal date format and serial number format (used internally by Excel).

## Use Cases

- **Billing Cycles**: Calculate the due date or the end of a billing period.
- **Financial Planning**: Find the end of fiscal periods.
- **Loan Calculations**: Determine the last day of interest periods or payment schedules.
- **Project Deadlines**: Establish month-end deadlines for deliverables.

The `EOMONTH` function is a simple yet powerful tool in Excel that makes it easy to work with month-end dates, whether
you're working with financial datasets, scheduling systems, or project timelines.