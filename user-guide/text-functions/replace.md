<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Explanation of the Excel `REPLACE` Function

The `REPLACE` function in Excel is used to replace part of a text string based on the position and length of the
substring you want to replace. This is useful for modifying text strings by removing or substituting specific segments.

#### Syntax:

```excel
REPLACE(old_text, start_num, num_chars, new_text)
```

#### Parameters:

1. **old_text**: The original text string from which you want to replace a part.
2. **start_num**: The position (character index) in `old_text` where you want to begin replacing characters. The first
   character is indexed as 1.
3. **num_chars**: The number of characters to replace in `old_text`.
4. **new_text**: The text you want to insert in place of the replaced characters.

#### Example:

Suppose cell `A1` contains the text `HelloWorld`.

1. To replace `World` with `Excel`, you can use:
   ```excel
   =REPLACE(A1, 6, 5, "Excel")
   ```
   **Result**: `HelloExcel`

2. To replace the first 3 characters with `Hi`:
   ```excel
   =REPLACE(A1, 1, 3, "Hi")
   ```
   **Result**: `HiLowWorld`

#### Use Case:

The `REPLACE` function is particularly helpful when dealing with structured text, such as replacing parts of IDs,
formatting phone numbers, or cleaning up data.

#### Note:

If `start_num` or `num_chars` exceed the length of `old_text`, the function will replace as many characters as it can
starting from `start_num`. If `new_text` is left blank (e.g. `""`), the specified part of `old_text` will be deleted.