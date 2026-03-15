<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    CODE(text)

- **text**: A required argument that refers to a single character or the first character in a string for which you want
  to obtain the numeric ASCII (or ANSI) code.

### Description:

The `CODE` function in Excel returns the numeric code corresponding to the first character of the text string it is
given. The returned value is based on the character encoding used by your system:

- On Windows, it typically provides the ANSI character code.
- On macOS, it provides the Macintosh character set code.

This function is helpful when you're working with text processing tasks, such as converting characters to their numeric
representations, or when validating certain character inputs.

### Examples:

1. **Basic Example - Single Character:**
   ```excel
   =CODE("A")
   ```
    - Outputs: `65`, because the ASCII value of the letter "A" is 65.

2. **String Input (Uses First Character Only):**
   ```excel
   =CODE("Hello")
   ```
    - Outputs: `72`, because the ASCII value of the first character, "H", is 72.

3. **Lowercase vs. Uppercase Characters:**
   ```excel
   =CODE("a")
   =CODE("A")
   ```
    - Outputs for `"a"`: `97`, because lowercase "a" has an ASCII value of 97.
    - Outputs for `"A"`: `65`, because uppercase "A" has an ASCII value of 65.

4. **Special Characters:**
   ```excel
   =CODE("!")
   =CODE(" ")
   ```
    - Outputs for `"!"`: `33`, because "!" has the value 33.
    - Outputs for `" "` (space): `32`, because the space character has the value 32.

5. **Error Handling - Empty String:**
   ```excel
   =CODE("")
   ```
    - Results in an error (`#VALUE!`) since the function expects at least one character as an input.

### Notes:

- The `CODE` function only evaluates the first character of the provided text.
- If the input is a number instead of text, Excel automatically casts the number to text. For example:
   ```excel
   =CODE(9)
   ```
  Returns `57`, because the character "9" has an ASCII value of 57.
- The `CODE` function is particularly useful when paired with functions like `CHAR`, enabling bidirectional conversion
  between codes and characters.
- Returns system-specific results—ensure you check character codes for your specific operating environment, as results
  might differ slightly between Windows and macOS.