<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## INDEX Function

The `INDEX` function in Excel returns a value or the reference to a value from within a table or range. This function is powerful and versatile, often used for looking up values and creating dynamic ranges.

### Syntax:

    INDEX(array, row_num, [column_num], [area_num])


- **array**: A range of cells, or an array constant.
- **row_num**: The row number in the array from which to retrieve the value. If set to 0, the function returns the array of values for the entire column.
- **column_num** (optional): The column number in the array from which to retrieve the value. If omitted and `row_num` is set, the function returns the array of values for the entire row.
- **area_num** (optional): Used when referencing a range consisting of multiple areas. If omitted, the first area is used.

### Examples:

1. `=INDEX(A1:C3, 2, 3)` returns the value at the second row and third column of the range `A1:C3`, which is cell `C2`.
2. `=INDEX(A1:C3, 0, 2)` returns the entire second column in the range `A1:C3`.
3. If you have a named range `MyData`, `=INDEX(MyData, 4)` returns the value in the fourth row of `MyData` (assuming `MyData` is a single-column range).

> **Note**: `INDEX` is often used in combination with the `MATCH` function to perform more complex lookups based on criteria.
> **Note**: Note: If Index is used as an output field and the row_num or column_num is 0, then this will produce a list output.  If row_num is 0 and column_num is 0 this will produce an area output.  However, if the 0 is not the value 0 but comes in from an input or other function then the output will not be a list or area and only the first value will be set of the list or area.
> **Note**: The `area_num` parameter is currently not supported.