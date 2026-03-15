<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## LEFT Function

The `LEFT` function in Excel is a text function that allows users to extract a specified number of characters from the beginning (left side) of a text string. It is useful when you want to extract a portion of a string based on its position from the left.

### Syntax:

    LEFT(text, [num_chars])

- **text**: The text string from which you want to extract characters. This can be a direct string, a cell reference, or the result of another function.
- **num_chars** (optional): The number of characters to extract starting from the left side of the string. If omitted, it defaults to 1, meaning only the first character will be extracted.

### Key Details:
- If `num_chars` is greater than the length of the text string, the `LEFT` function will return the entire string without any error.
- If `num_chars` is set to 0, the result will be an empty string (`""`).
- If `num_chars` is negative or not an integer, Excel will return a `#VALUE!` error.

### Examples:

1. **Extracting the First Two Characters**:
    =LEFT("Excel", 2)

This formula will return "Ex", which are the first two characters of the text "Excel".

Default Behavior (Extracting the First Character):

    =LEFT("Excel")

Since num_chars is omitted, the formula will return "E", the first character of the text string "Excel".

Using a Cell Reference: If cell A1 contains the text "Product123", the formula:

    =LEFT(A1, 7)

will return "Product", extracting the first 7 characters from the value in cell A1.

Combining with Other Functions: You can use LEFT in combination with other Excel functions. For example:

    =LEFT(A1, FIND(" ", A1) - 1) 

This formula will extract the first word from a text string in cell A1 by finding the position of the first space and subtracting 1.

Using LEFT in Filtering:

When used in conjunction with the FILTER function, LEFT can be applied to filter rows based on whether the text in a cell starts with a specific substring. For example:

    =FILTER(A1:A10, LEFT(A1:A10, 3) = "Pro", "No matches found")

This formula filters the range A1:A10 to include only entries where the text starts with "Pro".

Example of Error Handling:

If you try to extract more characters than are available in the string, Excel will return the full string without error. For example:

    =LEFT("Excel", 10)

will still return "Excel" even though the text string contains fewer than 10 characters.

Note: The LEFT function is case-sensitive and returns the characters exactly as they appear in the text string. It is commonly used when parsing strings, such as separating first names from full names, or working with product codes or serial numbers.