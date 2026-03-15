<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    ARRAYTOTEXT(array, [format])

- **array**: The array or range of values that you want to convert into text.
- **format** (optional): Specifies the text format to return:
    - `0` (default): Generates implicit text, which is generally a compact, human-readable representation of the array.
    - `1`: Generates explicit text, including explicit syntax (e.g., curly braces `{}` to clearly represent arrays).

### Description:

The `ARRAYTOTEXT` function in Excel converts an array (or range) of values into a text string. This function is useful
when you need to display array data as a text representation or when working with dynamic arrays in formulas.

The format parameter allows control over how the output text is structured:

- **Implicit format (0)**: Provides a simple, human-readable text form of the array.
- **Explicit format (1)**: Provides a detailed text representation, which includes syntax for arrays, such as `{}` for
  defining arrays explicitly.

This function is commonly used for text manipulation, debugging formulas, or for generating array text in specific
formats.

### Examples:

1. **Basic Example (Implicit Format):**
   ```excel
   =ARRAYTOTEXT(A1:C1)
   ```
    - If `A1:C1` contains `{1, 2, 3}`, the function outputs: `"1 2 3"`

2. **Explicit Format with `ARRAYTOTEXT`:**
   ```excel
   =ARRAYTOTEXT(A1:C1, 1)
   ```
    - If `A1:C1` contains `{1, 2, 3}`, the function outputs: `"{1,2,3}"`  
      (the array is explicitly represented with curly braces and commas.)

3. **Multi-dimensional Array Example (Explicit Format):**
   ```excel
   =ARRAYTOTEXT(A1:C2, 1)
   ```
    - If `A1:C2` contains:
      ```
      1 2 3
      4 5 6
      ```
      The function outputs: `"{1; 2; 3; 4; 5; 6}"`  

4. **Default Behavior Omission of `format`:**
   ```excel
   =ARRAYTOTEXT(A1:C2)
   ```
    - Uses the implicit format.  
      If `A1:C2` contains: `{1, 2, 3; 4, 5, 6}`, this outputs: `"1 2 3 4 5 6"`

### Notes:

- The `ARRAYTOTEXT` function was introduced in Excel 365 and Excel 2021 as part of the modern dynamic array
  functionality.
- When using **explicit format** (`1`), the output will always use text syntax representation that respects array
  notation (e.g., `{}` for arrays, commas for columns, semicolons for rows).
- This function is particularly useful for debugging array formulas or visualizing results of dynamic arrays.
- If the array is empty, the function returns an empty string (`""`).
- Implicit format is more user-friendly, while explicit format is better for precise data representations.