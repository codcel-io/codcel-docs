<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# SEARCH Function

The `SEARCH` function in Excel is used to find the position of a specific substring within a text string. This function
is case-insensitive, which means it treats "A" and "a" as the same. It is particularly useful for finding text patterns
within strings, aiding in text processing and manipulation tasks.

## Syntax

    SEARCH(find_text, within_text, [start_num])

- `find_text`: The text you want to find. This can be a single character or a string.
- `within_text`: The text in which you want to search for the `find_text`.
- `start_num` (optional): The position in `within_text` to start the search. The default is 1, which makes the search
  start at the first character.

## Returns

The `SEARCH` function returns the character position of the first occurrence of `find_text` in `within_text`. If the
`find_text` is not found, it returns a `#VALUE!` error.

## Key Features

- **Case-Insensitive**: Unlike the `FIND` function, `SEARCH` does not differentiate between uppercase and lowercase
  letters.
- **Flexible Start Point**: By using the `start_num` argument, you can control where the search begins. This is useful
  for skipping over parts of the text.
- **Error Handling**: Useful in combination with functions like `IFERROR` to gracefully handle instances where the
  `find_text` is not found.

## Example

Suppose you want to find the position of the substring "cat" in the text "Concatenation".

    =SEARCH("cat", "Concatenation")

This formula returns 4, since "cat" begins at the fourth character of "Concatenation".

## Notes

- If `find_text` is not found, the `SEARCH` function will return the `#VALUE!` error. It is often useful to wrap the
  SEARCH function in an `IFERROR` function to handle errors gracefully.
- The `start_num` argument is useful if you're working with large text strings and only want to search beyond a certain
  point.
- `SEARCH` can be used for wildcard searches by incorporating the `*` wildcard to match any number of characters or `?`
  to match a single character.

## Wildcard Support

The `SEARCH` function supports wildcards to find text patterns:

1. **Asterisk (*)**: Matches any number of characters. For example, `SEARCH("cat*", "Concatenation")` would return 4.
2. **Question Mark (?)**: Matches any single character. For example, `SEARCH("c?t", "Concatenation")` would not find a
   match because "c" is followed by "a", not just any single character before "t".

## Handling Errors

To handle cases where the text is not found, wrap the `SEARCH` function in the `IFERROR` function:

    =IFERROR(SEARCH("dog", "Concatenation"), "Not found")

If "dog" is not found in "Concatenation", this formula returns "Not found" instead of an error.

## Comparison with FIND

- The `SEARCH` function is case-insensitive, while the `FIND` function is case-sensitive.
- If you need to differentiate between cases (upper and lower), consider using `FIND` instead of `SEARCH`.