<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DAYS360 Function

The `DAYS360` function in Excel calculates the number of days between two dates based on a 360-day year, which assumes
each month has 30 days. This function is frequently used in financial and accounting systems to simplify date
calculations.

## Syntax

```plaintext
DAYS360(start_date, end_date, [method])
```

- **`start_date`**: The starting date of the period. It must be in a valid Excel date format or a reference to a cell
  containing such a date.
- **`end_date`**: The ending date of the period. It must also be in a valid Excel date format or a reference to a cell
  containing such a date.
- **`method`** (optional): A logical value (`TRUE` or `FALSE`) specifying the method to use:
    - `FALSE` or omitted: Uses the **US (NASD) method**, where the first day of a month and the last day of a month are
      handled differently.
    - `TRUE`: Uses the **European method**, where dates are treated consistently, and all months are assumed to have 30
      days.

## Returns

The `DAYS360` function returns an integer that represents the number of days between the two dates based on the chosen
360-day year model.

## Key Features

- **Simplified Date Diff**: Approximates the duration between two dates using a uniform 360-day year.
- **Choice of Method**: Supports both US and European calculation methods for compatibility with different financial
  systems.
- **Handles Edge Cases**: Specific rules account for irregularities like end-of-month dates.

## Example Usage

### Example 1: Default (US NASD Method)

Suppose you have two dates in cells `A1` (`2023-01-01`) and `A2` (`2023-12-31`).

```plaintext
=DAYS360(A1, A2)
```

This formula returns `360`, assuming the US method.

### Example 2: European Method

If you want to use the European method for these same dates:

```plaintext
=DAYS360(A1, A2, TRUE)
```

This formula also returns `360`, but it treats the dates using European rules.

### Example 3: End-of-Month Edge Case

For US-specific handling of end dates like January 30 and February 28:

```plaintext
=DAYS360(DATE(2023,1,30), DATE(2023,2,28))
```

This formula returns `30` if using the default US method.

## Notes

- Both `start_date` and `end_date` must be valid dates. Invalid dates will result in a `#VALUE!` error.
- Typically used in financial and accounting applications that require uniform month lengths (12 months x 30 days = 360
  days/year).
- The function simplifies interest calculations, payment schedules, and other financial planning tasks.

## Use Cases

- **Loan and Lease Agreements**: Compute daily interest and payment periods based on a standardized 30-day month.
- **Financial Forecasting**: Provides more predictable calculations for accounts payable/receivable timelines.
- **Accounting Systems**: Aligns with financial standards that use a 360-day year to harmonize date differences.

The `DAYS360` function is a specialized tool designed for consistent, predictable date-based calculations in financial
models and accounting software.