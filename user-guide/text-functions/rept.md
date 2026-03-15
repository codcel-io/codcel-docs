<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Explanation of the Excel `REPT` Function

The `REPT` function in Excel is used to repeat a text string a specified number of times. This is particularly useful
for generating repeated patterns or filling cells with repeated characters.

#### Syntax:

```excel
REPT(text, number_times)
```

#### Parameters:

1. **text**: The text string that you want to repeat.
2. **number_times**: The number of times that you want the text string to be repeated. It must be a positive integer.

#### Example:

Suppose cell `A1` contains the text `*`.

1. To repeat `*` 10 times, you can use:
   ```excel
   =REPT(A1, 10)
   ```
   **Result**: `**********`

2. To repeat the word `Hello` 3 times with no spaces:
   ```excel
   =REPT("Hello", 3)
   ```
   **Result**: `HelloHelloHello`

#### Use Case:

The `REPT` function is particularly helpful in tasks such as creating visual indicators (e.g., bar charts using
characters), formatting output data, or even creating placeholder text.

#### Note:

- If `number_times` is 0, the function will return an empty string (`""`).
- The function will return a `#VALUE!` error if `number_times` is a negative value or not a valid number.