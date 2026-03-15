<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# FILTER Function

The `FILTER` function in Excel is designed to filter a range of data based on the criteria you specify and return an array of matching entries. 
This powerful function is part of Excel's dynamic array functions, making it incredibly useful for extracting specific information from a larger dataset without the need for complex formulas or VBA code.

## Syntax

    FILTER(array, include, [if_empty])

- `array`: The range or array you want to filter.
- `include`: The array or condition that determines which elements to include in the result. This argument should return an array of TRUE or FALSE values, where TRUE indicates that the corresponding element in the `array` should be included in the output.
- `if_empty` (optional): The value to return if no records meet the criteria. If this parameter is omitted and no matches are found, the function will return the `#CALC!` error.

## Returns

The `FILTER` function returns an array of values that meet the specified criteria. If the `if_empty` parameter is provided, that value will be returned when no records meet the condition.

## Key Features

- **Dynamic Array Function**: As a dynamic array function, `FILTER` automatically spills the results over adjacent cells vertically or horizontally, depending on the shape of the returned array.
- **Versatile Criteria**: The `include` argument allows for complex logical conditions, enabling sophisticated filtering that can adapt to dynamic ranges and conditions.
- **No need for helper columns**: Unlike traditional filtering methods in Excel, the `FILTER` function doesn't require setting up additional columns for criteria checks.

## Example

Suppose you have a list of sales data in cells A1:B10, where column A contains salesperson names, and column B contains sales amounts. You want to filter this list to show only sales above $500.

    =FILTER(A1:B10, B1:B10>500, "No sales above $500")


This formula filters the range `A1:B10` for rows where the sales amount in column B is greater than $500. If no sales exceed $500, it returns the text "No sales above $500".

## Notes

- The `FILTER` function is available in Excel for Microsoft 365, Excel for Microsoft 365 for Mac, and Excel for the web.
- Ensure that the `include` argument array dimensions match the `array` dimensions to avoid dimension mismatch errors.
- The `FILTER` function can handle arrays that result from other functions or formulas, making it highly versatile in complex data analysis tasks.

## Supported include

The second parameter in the `FILTER` function in Excel specifies the condition(s) that must be met for the filter to return a result. This can be a single condition or a combination of multiple conditions. 
Currently not all conditions are supported, if it is not supported then (NOT SUPPORTED) is written next to it.
Here's a list of potential conditions you could use in the second parameter:

## 1. Comparison Conditions
These conditions check if a cell value meets a specific comparison.

- `B1:B10 > 500`: Greater than 500   (TESTED in filter.xlxs)
- `B1:B10 >= 500`: Greater than or equal to 500 (TESTED in filter.xlxs)
- `B1:B10 < 500`: Less than 500               (TESTED in filter.xlxs)
- `B1:B10 <= 500`: Less than or equal to 500       (TESTED in filter.xlxs)
- `B1:B10 = 500`: Equal to 500                  (TESTED in filter.xlxs)
- `B1:B10 <> 500`: Not equal to 500            (TESTED in filter.xlxs)

## 2. Text Conditions
These are useful for filtering based on text values.

- `A1:A10 = "Product A"`: Cells in `A1:A10` that are exactly equal to `"Product A"`.   (TESTED in filter.xlxs)
- `A1:A10 <> "Product A"`: Cells in `A1:A10` that are not equal to `"Product A"`       (TESTED in filter.xlxs)
- `ISNUMBER(SEARCH("Product", A1:A10))`: Cells in `A1:A10` that contain the text `"Product"` (case-insensitive)   (TESTED in filter.xlxs)

## 3. Logical (AND, OR) Conditions
You can combine multiple conditions using logical operators.

- `((B1:B10 > 500) * (A1:A10 = "Product A"))`: Sales above 500 **AND** Product A     (TESTED in filter.xlxs)
- `((B1:B10 > 500) + (A1:A10 = "Product B"))`: Sales above 500 **OR** Product B      (TESTED in filter.xlxs)

The `*` operator works as an "AND" (both conditions must be true), and the `+` operator works as an "OR" (at least one condition must be true).

## 4. Blank/Non-Blank Conditions
Useful for filtering out blank or non-blank cells.

- `B1:B10 <> ""`: Cells in `B1:B10` that are not blank     (TESTED in filter.xlxs)
- `A1:A10 = ""`: Cells in `A1:A10` that are blank          (TESTED in filter.xlxs)

## 5. Date Conditions
These conditions filter based on dates.

- `A1:A10 > DATE(2023,1,1)`: Dates after January 1, 2023   (TESTED in filter.xlxs)
- `A1:A10 < TODAY()`: Dates before today            (TESTED in filter.xlxs)
- `A1:A10 = DATE(2023,1,1)`: Dates exactly equal to January 1, 2023      (TESTED in filter.xlxs)   

## 6. Errors Handling
You can filter based on errors.

- `ISERROR(A1:A10)`: Cells that contain errors   (NOT SUPPORTED)
- `NOT(ISERROR(A1:A10))`: Cells that do not contain errors     (NOT SUPPORTED)

## 7. Non-Empty Numeric Conditions
You can filter cells that contain numbers using the `ISNUMBER` function.

- `ISNUMBER(B1:B10)`: Cells in `B1:B10` that contain numbers      (NOT SUPPORTED)
- `NOT(ISNUMBER(B1:B10))`: Cells that do not contain numbers        (NOT SUPPORTED)

## 8. Using Functions for Conditions
You can use Excel functions within the condition.

- `LEN(A1:A10) > 5`: Cells in `A1:A10` where the text length is greater than 5 characters   (TESTED in filter.xlxs)
- `MOD(B1:B10, 2) = 0`: Cells in `B1:B10` that contain even numbers                     (TESTED in filter.xlsx)

## 9. Multiple Columns Conditions
You can filter based on values across multiple columns.

- `((B1:B10 > 500) * (C1:C10 = "Yes"))`: Sales above 500 **AND** column C contains "Yes"     (TESTED in filter.xlxs)
- `((A1:A10 = "Product A") + (B1:B10 < 200))`: Product A **OR** sales less than 200        (TESTED in filter.xlxs)

## 10. Starts with

Let's say you want to filter values in the range `A1:A10` where the text starts with `"Prod"`.

The formula would look like this:

    =FILTER(A1:A10, LEFT(A1:A10, 4) = "Prod", "No matches found")    (TESTED in filter.xlxs) 

Explanation:

- LEFT(A1:A10, 4) extracts the first 4 characters of each value in A1:A10.
- The condition LEFT(A1:A10, 4) = "Prod" checks whether those first 4 characters are "Prod".
- FILTER returns the rows that meet this condition, or the message "No matches found" if none do.

Dynamic Character Length:

If you want the condition to check based on a dynamic starting value length (rather than a fixed number of characters), you can replace 4 with LEN("Prod"):

    =FILTER(A1:A10, LEFT(A1:A10, LEN("Prod")) = "Prod", "No matches found")  (TESTED in filter.xlxs)

This way, the formula adapts to the length of the text "Prod" automatically.

Summary:
You can use the LEFT function to filter values that start with a specific string, combined with FILTER to extract the matching rows.


## Mix and matched

These conditions can be mixed and matched depending on what data you want to filter out. The key is that any logical operation inside the second argument must result in a Boolean array (TRUE or FALSE), so the `FILTER` function knows which rows to keep.