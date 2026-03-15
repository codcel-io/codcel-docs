<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    SUBSTITUTE(text, old_text, new_text, [instance_num])

- **text**: The original text string in which you want to substitute text.
- **old_text**: The text string you want to replace in the original text.
- **new_text**: The text string you want to insert in place of the `old_text`.
- **instance_num**: *(Optional)* Specifies which instance of `old_text` to replace. If omitted, all instances of
  `old_text` are replaced.

### Description:

The `SUBSTITUTE` function in Excel replaces occurrences of a specific text string (`old_text`) in a given text (`text`)
with another text string (`new_text`). If the `instance_num` argument is provided, only that specific occurrence is
replaced. This function is useful for dynamic text replacement in data cleaning, formatting, or transformation tasks.

### Examples:

1. `=SUBSTITUTE("apple, orange, apple", "apple", "banana")`  
   Result: `banana, orange, banana`. Replaces all occurrences of `"apple"` with `"banana"`.

2. `=SUBSTITUTE("2023-10-15", "-", "/")`  
   Result: `2023/10/15`. Replaces all dashes (`-`) with slashes (`/`).

3. `=SUBSTITUTE("apple, orange, apple", "apple", "banana", 2)`  
   Result: `apple, orange, banana`. Replaces only the **second** occurrence of `"apple"` with `"banana"`.

4. `=SUBSTITUTE("aaa", "a", "b")`  
   Result: `bbb`. Replaces all occurrences of `"a"` with `"b"`.

5. `=SUBSTITUTE("abcdefabc", "abc", "xyz", 1)`  
   Result: `xyzdefabc`. Replaces only the **first** occurrence of `"abc"` with `"xyz"`.

### Notes:

- Unlike `REPLACE`, which is position-based, `SUBSTITUTE` works by matching exact text strings.
- The `instance_num` parameter is highly useful when you need to limit the number of substitutions.
- When `SUBSTITUTE` is applied to a case-sensitive text, ensure that the `old_text` matches exactly (including case).
- It can be combined with functions like `TRIM`, `FIND`, or `LEN` for advanced text manipulation scenarios.
- The function can handle both single-character replacements and longer substring replacements efficiently.