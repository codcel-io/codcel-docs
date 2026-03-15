<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Information Functions

This contains the list of information functions that are currently supported by Codcel.

## C

### [CELL](./information-functions/cell.md)

Returns information about the formatting, location, or contents of a cell.

- **Purpose:** Retrieves metadata about a cell — such as its address, row, column, data type, width, filename, or protection status — controlled by an `info_type` text string.
- **Formula:** `CELL(info_type, [reference])`
    - `info_type` is a text string specifying what information to return (e.g., `"address"`, `"row"`, `"col"`, `"type"`, `"contents"`, `"filename"`, `"width"`, `"protect"`).
    - `reference` (optional) is the cell to inspect; if omitted, uses the last-changed cell.
- **Example Usage:**
    - `=CELL("address", B5)` returns `$B$5` (absolute cell address as text)
    - `=CELL("row", D10)` returns `10` (row number of the referenced cell)
    - `=CELL("type", A1)` returns `"l"` for text, `"v"` for value, or `"b"` for blank
    - `=CELL("filename", A1)` returns the full file path, workbook name, and sheet name

## D

### [DROP](./information-functions/drop.md)

Excludes a specified number of rows or columns from the beginning or end of an array or range.

- **Purpose:** Removes the first or last N rows and/or columns from a dataset, useful for removing headers, trimming data, or extracting middle sections when combined with TAKE.
- **Formula:** `DROP(array, rows, [columns])`
    - `array` is the array or range from which to exclude rows and/or columns.
    - `rows` is the number of rows to exclude (positive for top, negative for bottom).
    - `columns` (optional) is the number of columns to exclude (positive for left, negative for right).
- **Example Usage:**
    - `=DROP(A1:C10, 2)` returns rows 3-10 with all columns (removes first 2 rows)
    - `=DROP(A1:C10, -3)` returns rows 1-7 with all columns (removes last 3 rows)
    - `=DROP(A1:D10, 1, 1)` returns rows 2-10 and columns B-D (removes first row and column)
    - `=DROP(SORT(A1:B10, 2, -1), 3)` sorts and removes the top 3 rows

## I

### [ISBLANK](./information-functions/isblank.md)

Checks whether a cell is empty, returning TRUE if the cell contains no data and FALSE otherwise.

- **Purpose:** Determines if a cell is completely empty (no value, formula, or content), enabling input validation, default value handling, and missing data detection.
- **Formula:** `ISBLANK(value)`
    - `value` is the cell reference or value you want to test for being blank.
- **Example Usage:**
    - `=ISBLANK(A1)` returns `TRUE` if A1 is completely empty
    - `=ISBLANK(A1)` returns `FALSE` if A1 contains `0`, `""`, text, or any other value
    - `=IF(ISBLANK(A1), "No data", A1)` returns `"No data"` if A1 is empty, otherwise returns the value in A1
    - `=IF(AND(ISBLANK(A1), ISBLANK(B1)), "Both empty", "Has data")` checks multiple cells for blankness

### [ISERR](./information-functions/iserr.md)

Checks whether a value is any error except #N/A, returning TRUE for errors like #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, and #NULL!.

- **Purpose:** Detects formula errors while excluding #N/A, enabling selective error handling that separates calculation errors from "not found" results in lookups.
- **Formula:** `ISERR(value)`
    - `value` is the value or expression you want to test for an error (excluding #N/A).
- **Example Usage:**
    - `=ISERR(1/0)` returns `TRUE` (division by zero produces #DIV/0!)
    - `=ISERR(NA())` returns `FALSE` (#N/A is not detected by ISERR)
    - `=IF(ISERR(A1/B1), "Calculation error", A1/B1)` returns a fallback message for non-#N/A errors
    - `=SUMPRODUCT(--ISERR(A1:A10))` counts cells containing errors other than #N/A

### [ISERROR](./information-functions/iserror.md)

Checks whether a value is any error, returning TRUE for all error types including #N/A, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, and #NULL!.

- **Purpose:** Detects any formula error, enabling universal error handling that catches all error types in a single check.
- **Formula:** `ISERROR(value)`
    - `value` is the value or expression you want to test for any error.
- **Example Usage:**
    - `=ISERROR(1/0)` returns `TRUE` (division by zero produces #DIV/0!)
    - `=ISERROR(NA())` returns `TRUE` (unlike ISERR, ISERROR detects #N/A)
    - `=IF(ISERROR(A1/B1), "Error", A1/B1)` returns a fallback message for any error
    - `=SUMPRODUCT(--ISERROR(A1:A10))` counts cells containing any error

### [ISOMITTED](./information-functions/isomitted.md)

Checks whether an argument was omitted in a LAMBDA function, returning TRUE if omitted and FALSE if provided.

- **Purpose:** Detects whether an optional parameter was supplied when a LAMBDA function was called, enabling default value handling and flexible function design.
- **Formula:** `ISOMITTED(argument)`
    - `argument` is the LAMBDA parameter you want to check for omission.
- **Example Usage:**
    - `=LAMBDA(x, y, IF(ISOMITTED(y), 10, y))(5)` returns `10` (uses default since y is omitted)
    - `=LAMBDA(name, greeting, IF(ISOMITTED(greeting), "Hello", greeting) & ", " & name)("Alice")` returns `"Hello, Alice"`
    - `=LAMBDA(val, mult, val * IF(ISOMITTED(mult), 2, mult))(10, 3)` returns `30` (uses provided multiplier)
    - `ISOMITTED` returns `FALSE` for empty strings, zero, and FALSE values — only truly omitted arguments return `TRUE`

## N

### [N](./information-functions/n.md)

Converts values to numbers, returning numeric equivalents for dates, logical values, and zero for text values.

- **Purpose:** Converts various data types to their numeric equivalents, ensuring numeric calculations work correctly.
- **Formula:** `N(value)`
    - `value` is the value you want to convert to a number (can be number, text, logical value, date, time, or cell
      reference).
- **Example Usage:**
    - `=N(42)` returns `42` (numbers remain unchanged)
    - `=N("Hello")` returns `0` (text values become zero)
    - `=N(TRUE)` returns `1` (TRUE becomes 1, FALSE becomes 0)
    - `=N("1/1/2024")` returns the date serial number `45292`
    - `=N({TRUE, "Text", 42, FALSE})` returns array `{1, 0, 42, 0}`

### [NA](./information-functions/na.md)

Returns the #N/A error value to indicate that data is not available.

- **Purpose:** Intentionally returns the #N/A error to mark cells where data is missing or not applicable, preventing blank cells from being misinterpreted in calculations.
- **Formula:** `NA()`
    - This function takes no arguments.
- **Example Usage:**
    - `=NA()` returns `#N/A`
    - `=IF(A1="", NA(), A1)` returns #N/A if A1 is empty, otherwise returns A1
    - `=ISNA(NA())` returns `TRUE`
    - `=IFNA(VLOOKUP("Unknown", A1:B10, 2, FALSE), "Not Found")` handles #N/A from failed lookups

## T

### [TAKE](./information-functions/take.md)

Extracts a specified number of rows or columns from the beginning or end of an array or range.

- **Purpose:** Retrieves the first or last N rows and/or columns from a dataset, useful for top/bottom analysis and data subsetting.
- **Formula:** `TAKE(array, rows, [columns])`
    - `array` is the array or range from which to extract rows and/or columns.
    - `rows` is the number of rows to extract (positive for top, negative for bottom).
    - `columns` (optional) is the number of columns to extract (positive for left, negative for right).
- **Example Usage:**
    - `=TAKE(A1:C10, 3)` returns the first 3 rows with all columns
    - `=TAKE(A1:C10, -2)` returns the last 2 rows with all columns
    - `=TAKE(A1:D10, 5, 2)` returns the first 5 rows and first 2 columns
    - `=TAKE(SORT(A1:B10, 2, -1), 5)` returns the top 5 rows after sorting by column 2 descending

### [TYPE](./information-functions/type.md)

Returns a number indicating the data type of a value.

- **Purpose:** Identifies the data type of a value by returning a numeric code (1 for number, 2 for text, 4 for logical, 16 for error, 64 for array), enabling type-aware logic in formulas.
- **Formula:** `TYPE(value)`
    - `value` is the value whose data type you want to identify.
- **Example Usage:**
    - `=TYPE(42)` returns `1` (number)
    - `=TYPE("Hello")` returns `2` (text)
    - `=TYPE(TRUE)` returns `4` (logical value)
    - `=TYPE(NA())` returns `16` (error value)
    - `=TYPE({1,2,3})` returns `64` (array)