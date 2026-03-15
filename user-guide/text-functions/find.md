<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# FIND Function

The `FIND` function in Excel is used to find the position of a specific substring within a text string. This function is
case-sensitive, which means it distinguishes between "A" and "a". It is particularly useful for identifying exact text
patterns within strings, aiding in precise text processing and manipulation tasks.

## Syntax

```excel
FIND(find_text, within_text, [start_num])
```

- `find_text`: The text you want to find. This can be a single character or a string.
- `within_text`: The text in which you want to search for the `find_text`.
- `start_num` (optional): The position in `within_text` to start the search. The default is 1, which makes the search
  start at the first character.

## Returns

The `FIND` function returns the character position of the first occurrence of `find_text` in `within_text`. If the
`find_text` is not found, it returns a `#VALUE!` error.

## Key Features

- **Case-Sensitive**: Unlike the `SEARCH` function, `FIND` differentiates between uppercase and lowercase letters.
- **Precise Searches**: Ideal for scenarios where exact matches are necessary, such as case-specific text extraction.
- **Flexible Start Point**: By using the `start_num` argument, you can control where the search begins, which is useful
  for skipping over parts of the text.

## Example

Suppose you want to find the position of the substring "Cat" in the text "Concatenation".

```excel
=FIND("Cat", "Concatenation")
```

This formula returns a `#VALUE!` error because "Cat" with uppercase 'C' is not present in "Concatenation".

To get a valid result:
Suppose you search for the substring "cat":

```excel
=FIND("cat", "Concatenation")
```

This formula returns 4, since "cat" begins at the fourth character of "Concatenation".

## Notes

- If `find_text` is not found, the `FIND` function will return the `#VALUE!` error. It is often useful to wrap the FIND
  function in an `IFERROR` function to handle errors gracefully.
- The `start_num` argument is useful if you're working with large text strings and only want to search beyond a certain
  point.

## Handling Errors

To handle cases where the text is not found, wrap the `FIND` function in the `IFERROR` function:

```excel
=IFERROR(FIND("dog", "Concatenation"), "Not found")
```

If "dog" is not found in "Concatenation", this formula returns "Not found" instead of an error.

## Comparison with SEARCH

- The `FIND` function is case-sensitive, while the `SEARCH` function is case-insensitive.
- If you need to differentiate between cases (upper and lower), consider using `FIND` instead of `SEARCH`.