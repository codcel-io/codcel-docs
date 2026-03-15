<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RIGHT Function

The `RIGHT` function in Excel is a text function that allows users to extract a specified number of characters from the
end (right side) of a text string. It is useful when you want to extract a portion of a string based on its position
from the right.

### Syntax:

    RIGHT(text, [num_chars])

- **text**: The text string from which you want to extract characters. This can be a direct string, a cell reference, or
  the result of another function.
- **num_chars** (optional): The number of characters to extract starting from the right side of the string. If omitted,
  it defaults to 1, meaning only the last character will be extracted.

### Key Details:

- If `num_chars` is greater than the length of the text string, the `RIGHT` function will return the entire string
  without any error.
- If `num_chars` is set to 0, the result will be an empty string (`""`).
- If `num_chars` is negative or not an integer, Excel will return a `#VALUE!` error.

### Examples:

1. **Extracting the Last Three Characters**:
    ```excel
    =RIGHT("Excel", 3)
    ```
   This formula will return "cel", which are the last three characters of the text "Excel".

2. **Default Behavior (Extracting the Last Character)**:
    ```excel
    =RIGHT("Excel")
    ```
   Since `num_chars` is omitted, the formula will return "l", the last character of the text string "Excel".

3. **Using a Cell Reference**:  
   If cell A1 contains the text "Product123", the formula:
    ```excel
    =RIGHT(A1, 3)
    ```
   will return "123", extracting the last 3 characters from the value in cell A1.

4. **Combining with Other Functions**:  
   You can use `RIGHT` in combination with other functions. For example:
    ```excel
    =RIGHT(A1, LEN(A1) - FIND("-", A1))
    ```
   This formula extracts all characters after a hyphen ("-") in a string. It calculates the number of characters to
   extract based on the position of the hyphen.

5. **Using RIGHT for Substring Matching**:
    ```excel
    =FILTER(A1:A10, RIGHT(A1:A10, 3) = "123", "No matches found")
    ```
   This formula filters the range A1:A10 to include only entries where the last 3 characters of the text are "123".

6. **Handling Too Many Characters**:  
   If you try to extract more characters than are available in the string, the `RIGHT` function will still return the
   full string. For example:
    ```excel
    =RIGHT("Excel", 10)
    ```
   will return "Excel" even though the text string contains fewer than 10 characters.

### Notes:

- The `RIGHT` function is case-sensitive and returns the characters exactly as they appear in the text string.
- It is commonly used in data parsing tasks, such as extracting file extensions, suffixes, or parts of product codes.

By combining `RIGHT` with other functions like `LEN` and `FIND`, you can perform advanced text string manipulations with
ease.