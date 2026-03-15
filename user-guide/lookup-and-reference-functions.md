<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->


## A

### [ADDRESS](./lookup-and-reference-functions/address.md)
Creates a cell address as a text string from a row and column number.

- **Purpose:** Constructs a cell reference in A1-style or R1C1-style notation, with options for absolute or relative referencing and optional sheet name qualification.

- **Formula:** `ADDRESS(row_num, column_num, [abs_num], [a1], [sheet_text])`
    - `row_num` is the row number to use in the cell reference.
    - `column_num` is the column number to use in the cell reference.
    - `abs_num` (optional) specifies the reference type: 1 = absolute (default), 2 = absolute row/relative col, 3 = relative row/absolute col, 4 = relative.
    - `a1` (optional) specifies reference style: TRUE = A1-style (default), FALSE = R1C1-style.
    - `sheet_text` (optional) is the worksheet name to include as a prefix.

- **Example Usage:**
    - `=ADDRESS(1, 1)` returns `$A$1`.
    - `=ADDRESS(3, 2, 4)` returns `B3` (fully relative).
    - `=ADDRESS(1, 1, 1, TRUE, "Sales")` returns `Sales!$A$1`.
    - `=INDIRECT(ADDRESS(2, 3))` returns the value in cell C2.

### [AREAS](./lookup-and-reference-functions/areas.md)
Returns the number of areas in a reference.

- **Purpose:** Counts the number of distinct contiguous ranges (areas) within a reference, useful for validating references and building dynamic formulas that adapt to multi-area inputs.

- **Formula:** `AREAS(reference)`
    - `reference` is a reference to a cell, range, or multiple ranges. Multiple areas must be enclosed in extra parentheses, e.g., `(A1:B2, C3:D4)`.

- **Example Usage:**
    - `=AREAS(A1:D5)` returns 1 (single contiguous range).
    - `=AREAS((A1:B2, C3:D4, E5:F6))` returns 3 (three separate areas).
    - `=AREAS((A1, B1, C1, D1))` returns 4 (four single-cell areas).
    - `=IF(AREAS(MyRange) > 1, "Multiple areas", "Single area")` checks if a named range has multiple areas.

## C

### [CHOOSE](./lookup-and-reference-functions/choose.md)
Returns a value from a list based on a given index number.

- **Purpose:** Selects one value or range from a list of options using a numeric index.

- **Formula:** CHOOSE(index_num, value1, [value2], …)
  - **index_num** is a number from 1 to 254 indicating which value to return.
  - **value1, value2, …** are the possible values or ranges to choose from.

- **Example Usage:**
  - =CHOOSE(2, "Red", "Green", "Blue") returns "Green".
  - =CHOOSE(A1, 10, 20, 30) returns 20 if A1 is 2.
  - =SUM(CHOOSE(1, A1:A3, B1:B3)) returns the sum of A1:A3.

### [CHOOSECOLS](./lookup-and-reference-functions/choosecols.md)
Returns specified columns from an array or range.

- **Purpose:** Extracts one or more columns by index, allowing column selection, reordering, and duplication.

- **Formula:** `CHOOSECOLS(array, col_num1, [col_num2], …)`
    - `array` is the array or range from which to return columns.
    - `col_num1, col_num2, …` are the column indices to return (positive from left, negative from right).

- **Example Usage:**
    - `=CHOOSECOLS(A1:D5, 2)` returns only the second column.
    - `=CHOOSECOLS(A1:D5, 4, 2, 1)` returns columns in order: D, B, A.
    - `=CHOOSECOLS(A1:D5, -1)` returns the last column.
    - `=CHOOSECOLS(A1:C5, 1, 2, 2, 3)` returns columns A, B, B, C (B duplicated).

### [CHOOSEROWS](./lookup-and-reference-functions/chooserows.md)
Returns specified rows from an array or range.

- **Purpose:** Extracts one or more rows by index, allowing row selection, reordering, and duplication.

- **Formula:** `CHOOSEROWS(array, row_num1, [row_num2], …)`
    - `array` is the array or range from which to return rows.
    - `row_num1, row_num2, …` are the row indices to return (positive from top, negative from bottom).

- **Example Usage:**
    - `=CHOOSEROWS(A1:D5, 2)` returns only the second row.
    - `=CHOOSEROWS(A1:D5, 5, 3, 1)` returns rows in order: 5, 3, 1.
    - `=CHOOSEROWS(A1:D5, -1)` returns the last row.
    - `=CHOOSEROWS(A1:D5, 1, 2, 2, 3)` returns rows 1, 2, 2, 3 (row 2 duplicated).

### [COLUMN](./lookup-and-reference-functions/column.md)
Returns the column number of a cell reference.

- **Purpose:** Returns the column number of a given reference, or the column number of the cell containing the formula if no reference is provided.

- **Formula:** `COLUMN([reference])`
    - `reference` (optional) is a cell or range for which you want the column number.

- **Example Usage:**
    - `=COLUMN(C1)` returns 3.
    - `=COLUMN()` returns the column number of the cell containing the formula.
    - `=COLUMN(D5:F10)` returns 4 (the first column in the range).
    - `=ADDRESS(ROW(), COLUMN())` returns the address of the current cell.

### [COLUMNS](./lookup-and-reference-functions/columns.md)
Returns the number of columns in a reference or array.

- **Purpose:** Counts the total number of columns in a range, array, or reference, useful for dynamic formulas and determining array dimensions.

- **Formula:** `COLUMNS(array)`
    - `array` is a reference, array constant, or range for which you want the number of columns.

- **Example Usage:**
    - `=COLUMNS(A1:D1)` returns 4.
    - `=COLUMNS(A1:D5)` returns 4.
    - `=COLUMNS({1,2,3;4,5,6;7,8,9})` returns 3.
    - `=ROWS(A1:D10) * COLUMNS(A1:D10)` returns the total cell count (40).

## E

### [EXPAND](./lookup-and-reference-functions/expand.md)
Expands an array to specified dimensions, filling new positions with a pad value.

- **Purpose:** Increases array dimensions by adding rows and/or columns, useful for aligning arrays of different sizes for calculations.

- **Formula:** `EXPAND(array, rows, [columns], [pad_with])`
    - `array` is the array or range to expand.
    - `rows` is the number of rows in the expanded array.
    - `columns` (optional) is the number of columns in the expanded array.
    - `pad_with` (optional) is the value to fill new cells (defaults to `#N/A`).

- **Example Usage:**
    - `=EXPAND({1,2;3,4}, 4, 4, 0)` expands a 2x2 array to 4x4, padding with zeros.
    - `=EXPAND(A1:B2, 5, , 0)` expands to 5 rows, keeping original columns, padding with 0.
    - `=EXPAND({"Apple","Banana"}, 2, 4, "N/A")` creates a 2x4 array with text padding.

## F

### [FORMULATEXT](./lookup-and-reference-functions/formula_text.md)
Returns a formula as a string.

- **Purpose:** Displays the formula in a referenced cell as text. Useful for documentation and formula auditing.

- **Formula:** FORMULATEXT(reference)
    - **reference** is the cell or range reference containing the formula to be displayed as text.

- **Example Usage:**
    - =FORMULATEXT(A1) returns "=SUM(B1:B5)" if A1 contains that formula
    - =FORMULATEXT(B2) returns "#N/A" if B2 contains a value instead of a formula
    - =FORMULATEXT($C$1) shows absolute reference formulas as text

## G

### [GROUPBY](./lookup-and-reference-functions/groupby.md)
Groups data by one or more row fields and aggregates values using a specified function.

- **Purpose:** Creates a summary table by grouping rows that share common values and applying an aggregation function (such as SUM, AVERAGE, or COUNT), producing pivot-table-style results directly in a formula.

- **Formula:** `GROUPBY(row_fields, values, function, [field_headers], [total_depth], [sort_order], [filter_array])`
    - `row_fields` is the column(s) used to group the data.
    - `values` is the column(s) containing data to aggregate for each group.
    - `function` is the aggregation function to apply (e.g., SUM, AVERAGE, COUNT, or a custom LAMBDA).
    - `field_headers` (optional) specifies whether headers are present and how to handle them (0 = no headers, 1 = yes but don't show, 2 = no but generate, 3 = yes and show).
    - `total_depth` (optional) controls grand total and subtotal display (0 = none, 1 = grand total at bottom, -1 = grand total at top, 2 or -2 = with subtotals).
    - `sort_order` (optional) specifies sort order: 0 = no sort, 1 = ascending, -1 = descending.
    - `filter_array` (optional) is a Boolean array that filters which rows to include before grouping.

- **Example Usage:**
    - `=GROUPBY(A2:A10, B2:B10, SUM)` groups by column A and sums the values in column B for each group.
    - `=GROUPBY(A1:A10, B1:B10, SUM, 3)` includes field headers in the output.
    - `=GROUPBY(A2:A10, B2:B10, SUM, , 1, -1)` adds a grand total and sorts descending.
    - `=GROUPBY(HSTACK(A2:A10, B2:B10), C2:C10, SUM)` groups by two columns using HSTACK.

## H

### [HSTACK](./lookup-and-reference-functions/h_stack.md) *(Coming soon)*
Stacks values horizontally into a single array row-wise, placing each array or value next to the previous.

- **Purpose:** Combines multiple arrays or values into a horizontal array. This is useful for aligning data from different sources into a single row-based structure.

- **Formula:** `HSTACK(array1, [array2], …)`
    - `array1, array2, …` are the values or arrays to be stacked. Scalars are treated as 1×1 arrays. Arrays with different row sizes are padded with blank cells as needed.

- **Example Usage:**
    - `=HSTACK("Apple", "Banana", "Cherry")` returns a horizontal array:
        ```
        Apple   Banana   Cherry
        ```
    - `=HSTACK(A1:A3, B1:B3)` stacks the two ranges side by side.
    - `=HSTACK({"A","B"}, "C", {"D";"E"})` results in:
        ```
        A   B   C   D
                    E
        ```

## O

### [OFFSET](./lookup-and-reference-functions/offset.md)
Returns a reference to a range that is offset from a starting cell by a specified number of rows and columns.

- **Purpose:** Dynamically constructs a cell or range reference by shifting from a starting point, with optional resizing. Ideal for creating flexible, sliding ranges.

- **Formula:** `OFFSET(reference, rows, cols, [height], [width])`
    - `reference` is the starting cell or range from which the offset is applied.
    - `rows` is the number of rows to move (positive = down, negative = up).
    - `cols` is the number of columns to move (positive = right, negative = left).
    - `height` (optional) is the number of rows in the returned reference.
    - `width` (optional) is the number of columns in the returned reference.

- **Example Usage:**
    - `=OFFSET(A1, 2, 3)` returns the value 2 rows down and 3 columns right of A1.
    - `=SUM(OFFSET(A1, 1, 0, 3, 2))` sums a 3-row by 2-column range starting from A2.
    - `=OFFSET(A1, 0, 0, COUNTA(A:A), 1)` creates a dynamic range that expands with data.
    - `=AVERAGE(OFFSET(A1, COUNTA(A:A) - 5, 0, 5, 1))` averages the last 5 values in column A.

## R

### [ROW](./lookup-and-reference-functions/row.md)
Returns the row number of a cell reference.

- **Purpose:** Returns the row number of a given reference, or the row number of the cell containing the formula if no reference is provided.

- **Formula:** `ROW([reference])`
    - `reference` (optional) is a cell or range for which you want the row number.

- **Example Usage:**
    - `=ROW(A5)` returns 5.
    - `=ROW()` returns the row number of the cell containing the formula.
    - `=ROW(B10:D15)` returns 10 (the first row in the range).
    - `=ADDRESS(ROW(), COLUMN())` returns the address of the current cell.

### [ROWS](./lookup-and-reference-functions/rows.md)
Returns the number of rows in a reference or array.

- **Purpose:** Counts the total number of rows in a range, array, or reference, useful for dynamic formulas and determining array dimensions.

- **Formula:** `ROWS(array)`
    - `array` is a reference, array constant, or range for which you want the number of rows.

- **Example Usage:**
    - `=ROWS(A1:A10)` returns 10.
    - `=ROWS(A1:D5)` returns 5.
    - `=ROWS({1,2,3;4,5,6;7,8,9})` returns 3.
    - `=ROWS(A1:D10) * COLUMNS(A1:D10)` returns the total cell count (40).

## S

### [SORT](./lookup-and-reference-functions/sort.md)
Sorts the contents of a range or array in ascending or descending order.

- **Purpose:** Sorts data in a range or array based on one or more columns, with options for ascending or descending order and row-wise or column-wise sorting.

- **Formula:** `SORT(array, [sort_index], [sort_order], [by_col])`
    - `array` is the range or array to sort.
    - `sort_index` (optional) is a number indicating the row or column to sort by. Defaults to 1.
    - `sort_order` (optional) is 1 for ascending (default) or -1 for descending.
    - `by_col` (optional) is `FALSE` (default) to sort by rows or `TRUE` to sort by columns.

- **Example Usage:**
    - `=SORT(A1:A10)` sorts the range in ascending order.
    - `=SORT(A1:C10, 2, -1)` sorts a table by the second column in descending order.
    - `=SORT(A1:C10, 1, 1, TRUE)` sorts a range by columns rather than rows.

### [SORTBY](./lookup-and-reference-functions/sortby.md)
Sorts a range or array based on the values in a corresponding range or array.

- **Purpose:** Sorts one dataset according to the values of another, supporting multiple sort keys and orders.

- **Formula:** `SORTBY(array, by_array1, [sort_order1], [by_array_n], [sort_order_n])`
    - `array` is the array or range to be sorted.
    - `by_array1` is the first array or range to sort by.
    - `sort_order1` (optional) is 1 for ascending (default) or -1 for descending.
    - `by_array_n, sort_order_n` (optional) are additional sort keys and orders.

- **Example Usage:**
    - `=SORTBY(A2:B5, B2:B5, 1)` sorts the range by column B in ascending order.
    - `=SORTBY(A2:C5, B2:B5, 1, C2:C5, -1)` sorts by column B ascending, then column C descending.

## T

### [TOCOL](./lookup-and-reference-functions/tocol.md)
Converts an array or range into a single column.

- **Purpose:** Flattens a multi-dimensional array into a single vertical column, with options to control scan order and filter blanks/errors.

- **Formula:** `TOCOL(array, [ignore], [scan_by_column])`
    - `array` is the array or range to convert to a single column.
    - `ignore` (optional) specifies what to ignore: 0 = keep all, 1 = ignore blanks, 2 = ignore errors, 3 = ignore both.
    - `scan_by_column` (optional) specifies scan order: FALSE = by row (default), TRUE = by column.

- **Example Usage:**
    - `=TOCOL(A1:C3)` returns all values from the range as a single column, scanned by row.
    - `=TOCOL(A1:C3, 0, TRUE)` scans by column instead of by row.
    - `=TOCOL(A1:C3, 1)` returns values as a column, ignoring blank cells.
    - `=TOCOL(A1:C3, 3)` ignores both blanks and errors.

### [TOROW](./lookup-and-reference-functions/torow.md)
Converts an array or range into a single row.

- **Purpose:** Flattens a multi-dimensional array into a single horizontal row, with options to control scan order and filter blanks/errors.

- **Formula:** `TOROW(array, [ignore], [scan_by_column])`
    - `array` is the array or range to convert to a single row.
    - `ignore` (optional) specifies what to ignore: 0 = keep all, 1 = ignore blanks, 2 = ignore errors, 3 = ignore both.
    - `scan_by_column` (optional) specifies scan order: FALSE = by row (default), TRUE = by column.

- **Example Usage:**
    - `=TOROW(A1:C3)` returns all values from the range as a single row, scanned by row.
    - `=TOROW(A1:C3, 0, TRUE)` scans by column instead of by row.
    - `=TOROW(A1:C3, 1)` returns values as a row, ignoring blank cells.
    - `=TOROW(A1:C3, 3)` ignores both blanks and errors.

### [TRANSPOSE](./lookup-and-reference-functions/transpose.md)
Rotates the orientation of a range or array, converting rows to columns and columns to rows.

- **Purpose:** Transforms data layout by swapping rows and columns, useful for restructuring data for different presentation or calculation needs.

- **Formula:** `TRANSPOSE(array)`
    - `array` is the array or range to transpose.

- **Example Usage:**
    - `=TRANSPOSE(A1:D1)` converts a horizontal row to a vertical column.
    - `=TRANSPOSE(A1:A4)` converts a vertical column to a horizontal row.
    - `=TRANSPOSE({1,2,3;4,5,6})` converts a 2×3 array to a 3×2 array.
    - `=TRANSPOSE(SEQUENCE(1, 5))` creates a vertical sequence from 1 to 5.

### [TRIMRANGE](./lookup-and-reference-functions/trimrange.md)
Removes empty rows and columns from the edges of an array or range.

- **Purpose:** Trims leading and trailing blank rows and columns from an array, returning a more compact result without affecting internal data.

- **Formula:** `TRIMRANGE(array)`
    - `array` is the array or range from which to remove empty edge rows and columns.

- **Example Usage:**
    - `=TRIMRANGE(A1:D6)` removes empty rows at top/bottom and empty columns at left/right.
    - `=TRIMRANGE(HSTACK(A1:B3, D1:E3))` cleans up empty edges after combining ranges.
    - `=TRIMRANGE(EXPAND(A1:B2, 5, 5, ""))` trims empty padding from an expanded array.
    - `=TRIMRANGE({""," ";" ","A"})` returns just "A" after trimming empty edges.

## U

### [UNIQUE](./lookup-and-reference-functions/unique.md)
Returns a list of unique values from a range or array.

- **Purpose:** Extracts distinct values, with options to compare by rows or columns and to return only values that appear exactly once.

- **Formula:** `UNIQUE(array, [by_col], [exactly_once])`
    - `array` is the range or array from which to extract unique values.
    - `by_col` (optional) is `TRUE` to compare by columns, `FALSE` or omitted to compare by rows.
    - `exactly_once` (optional) is `TRUE` to return only values appearing exactly once, `FALSE` or omitted to return all unique values.

- **Example Usage:**
    - `=UNIQUE(A1:A10)` returns a list of unique values from the range.
    - `=UNIQUE(B1:D1, TRUE)` returns unique values comparing across columns.
    - `=UNIQUE(A1:C3, FALSE, TRUE)` returns values that occur exactly once, comparing across rows.

## V

### [VSTACK](./lookup-and-reference-functions/v_stack.md) *(Coming soon)*
Stacks values vertically into a single array column-wise, aligning each array or value underneath the previous.

- **Purpose:** Combines multiple arrays or values into a vertical array. This is useful for merging data from different sources into a single column-based structure.

- **Formula:** `VSTACK(array1, [array2], …)`
    - `array1, array2, …` are the values or arrays to be stacked. Scalars are treated as 1×1 arrays. Arrays with different column sizes are padded with blank cells as needed.

- **Example Usage:**
    - `=VSTACK("Apple", "Banana", "Cherry")` returns a vertical array:
        ```
        Apple
        Banana
        Cherry
        ```
    - `=VSTACK(A1:A3, B1:B3)` stacks the two ranges vertically.
    - `=VSTACK({"A","B"}, {"C";"D"}, "E")` results in:
        ```
        A   B
        C
        D
        E
        ```

## W

### [WRAPCOLS](./lookup-and-reference-functions/wrapcols.md)
Wraps a row or column of values into a two-dimensional array by columns.

- **Purpose:** Reshapes a one-dimensional vector into a 2D array, filling column by column with a specified number of values per column.

- **Formula:** `WRAPCOLS(vector, wrap_count, [pad_with])`
    - `vector` is a row or column of values to wrap.
    - `wrap_count` is the maximum number of values per column (number of rows in result).
    - `pad_with` (optional) is the value to fill empty cells if the vector doesn't divide evenly (defaults to `#N/A`).

- **Example Usage:**
    - `=WRAPCOLS({1,2,3,4,5,6,7,8,9}, 3)` returns a 3×3 array filled by columns.
    - `=WRAPCOLS(A1:A12, 4)` wraps 12 values into 4-row columns.
    - `=WRAPCOLS(SEQUENCE(1,10), 5, 0)` wraps 10 numbers into 5-row columns, padding with 0.

### [WRAPROWS](./lookup-and-reference-functions/wraprows.md)
Wraps a row or column of values into a two-dimensional array by rows.

- **Purpose:** Reshapes a one-dimensional vector into a 2D array, filling row by row with a specified number of values per row.

- **Formula:** `WRAPROWS(vector, wrap_count, [pad_with])`
    - `vector` is a row or column of values to wrap.
    - `wrap_count` is the maximum number of values per row (number of columns in result).
    - `pad_with` (optional) is the value to fill empty cells if the vector doesn't divide evenly (defaults to `#N/A`).

- **Example Usage:**
    - `=WRAPROWS({1,2,3,4,5,6,7,8,9}, 3)` returns a 3×3 array filled by rows.
    - `=WRAPROWS(A1:A12, 4)` wraps 12 values into 4-column rows.
    - `=WRAPROWS(SEQUENCE(1,10), 5, 0)` wraps 10 numbers into 5-column rows, padding with 0.