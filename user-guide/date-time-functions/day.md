<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DAY Function

The `DAY` function in Excel is used to extract the day of the month from a given date value. It is particularly useful
for breaking down a date into its individual components when performing date analysis or calculations.

## Syntax

```plaintext
DAY(date)
```

- `date`: This is the date value or a reference to a cell containing a date from which you want to extract the
  day. The date must be in a valid Excel date format

## Returns

The `DAY` function returns an integer value representing the day of the month from the provided date. This value ranges
from 1 to 31, depending on the specific date in the `date`.

## Key Features

- **Date Component Extraction**: Enables retrieval of the day component from any given date.
- **Integration with Other Functions**: Can be combined with other date functions like `MONTH` and `YEAR` for
  comprehensive date analysis.
- **Supports Various Date Inputs**: Works with both cell references containing dates and direct date serial values.

## Example

Suppose you have a date in cell `A1` which is `2023-12-25`.

```plaintext
=DAY(A1)
```

This formula returns `25`, as the day of the date `December 25, 2023` is the 25th.

For a direct date serial number:

```plaintext
=DAY(DATE(2023, 12, 25))
```

This formula also returns `25`, extracting the day from the constructed date.

## Notes

- The `DAY` function is useful in scenarios where you need to isolate the day part of a date for reporting or decision
  logic.
- It is often used in conjunction with conditional functions to execute specific actions based on the day of the month.
- Ensure that the input is a valid date format recognized by Excel to avoid errors or unexpected results.

## Use Cases

- **Date Filtering**: Quickly filter records based on the day of a month, such as identifying all transactions occurring
  on the 15th of each month.
- **Day-Based Analysis**: Identifying patterns or trends tied to specific days within a dataset.

The `DAY` function provides an easy and efficient way to dissect date values for detailed analysis and logical
computations in Excel.