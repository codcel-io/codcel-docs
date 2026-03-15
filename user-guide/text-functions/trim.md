<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    TRIM(text)

- **text**: The text string from which you want to remove extra spaces.

### Description:

The `TRIM` function in Excel removes all extra spaces from a text string, leaving only single spaces between words. It
is typically used to clean up text data imported from external sources or to ensure consistency in text formatting. This
function is especially useful when working with data that may contain leading, trailing, or excess spaces internally.

### Examples:

1. `=TRIM("   Hello   World   ")`  
   Result: `Hello World`. Removes leading, trailing, and multiple spaces between words in the text.

2. `=TRIM("  Data Cleaning    is  important  ")`  
   Result: `Data Cleaning is important`. Produces a properly formatted text string by removing unnecessary spaces.

3. `=TRIM(A1)`  
   If cell `A1` contains `   Excel  is   great   `, the result will be `Excel is great`. Cleans up the text in cell
   `A1`.

4. `=TRIM(CONCATENATE("   Clean   ", "   Data   "))`  
   Result: `Clean Data`. Combines and cleans up text with proper spacing.

### Notes:

- The `TRIM` function removes all spaces except for single spaces within words, ensuring clear formatting.
- It does not affect non-breaking spaces, which may appear as extra spaces in text.
- Combine `TRIM` with other text functions like `UPPER`, `LOWER`, or `PROPER` for comprehensive text cleaning workflows.
- Useful for cleaning up imported data that may have irregular spacing issues.
- TRIM works for spaces as defined by the standard ASCII character set. Non-standard spaces may require additional
  processing or substitution functions.