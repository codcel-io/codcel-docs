<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DGET Function

The `DGET` function extracts a single value from a column of a database, where that value is the unique matching row's entry in the specified column.

### Syntax:

    DGET(database, field, criteria)

- **database**: A range whose first row contains column headers.
- **field**: The column to read the value from. Either the 1-based column number or the header label.
- **criteria**: A range describing the filter. Must select exactly one row.

### Examples:

1. `=DGET(A1:E11, "Salary", G1:G2)` where `G1:G2` is `Name` / `Alice` — returns `100` (Alice's salary).
2. `=DGET(A1:E11, "Manager", G1:G2)` — returns the boolean Manager flag for the uniquely matched row.
3. `=DGET(A1:E11, "Dept", G1:G2)` — returns the matched row's text Department.

### Usage Notes:

- Returns **#NUM!** if no rows match the criteria.
- Returns **#VALUE!** if more than one row matches.
- The returned value preserves its native type (number, text, boolean, etc.).
- Field lookup is case-insensitive.

> **Related**: [`VLOOKUP`](../table-functions/vlookup.md), [`XLOOKUP`](../table-functions/xlookup.md), [`FILTER`](../table-functions/filter.md).
