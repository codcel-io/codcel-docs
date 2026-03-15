<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# YEAR Function

The `YEAR` function in Excel is used to extract the year component from a date value. It is particularly useful when you
need to analyze or manipulate the year part of a date for reporting, calculations, or data management purposes.

## Syntax

    YEAR(date)

- `date`: This argument represents the date value from which the year is to be extracted. It can be a date that
  is input directly or a reference to a cell containing the date.

## Returns

The `YEAR` function returns a four-digit number representing the year portion of the specified date. This allows for
easy extraction and use in further calculations or data analysis.

## Key Features

- **Simple Year Extraction**: Provides a straightforward method to obtain the year from a complete date, aiding various
  data processing tasks.
- **Compatibility with Excel Dates**: Works seamlessly with Excel's date serial numbers, allowing for consistent and
  error-free year extraction.
- **Facilitates Year-Related Operations**: Useful in scenarios involving year comparisons, trend analysis, and
  time-related categorization.

## Example

Suppose you have a date representing March 15, 2023, stored in cell A1.

    =YEAR(A1)

This formula extracts and returns `2023` as the year from the date in cell A1.

When you need to directly input a date:

    =YEAR(DATE(2023, 3, 15))

This will also return `2023` since the `DATE` function constructs the date from its components, and `YEAR` subsequently
extracts the year.

## Notes

- The `YEAR` function is most effective when handling date values throughout calculations or data extractions requiring
  year information.
- It assumes that the input date is a valid serial number recognizable by Excel's date system.
- Ideal for use in scenarios where chronological data organization or filtering by year is required.

The `YEAR` function strengthens date handling capabilities by providing an effortless method to extract and utilize year
data within spreadsheets, enhancing time-based insights and management.