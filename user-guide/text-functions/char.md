<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    CHAR(number)

- **number**: A numeric value between 1 and 255 that represents an ASCII code.

### Description:

The `CHAR` function in Excel returns the character associated with the specified ASCII code. ASCII (American Standard
Code for Information Interchange) is a character encoding standard that maps numeric values to corresponding characters.
For example:

    CHAR(number) = character corresponding to ASCII code `number`

### Examples:

1. `=CHAR(65)` would return `A`, because the ASCII code 65 corresponds to the character `A`.
2. `=CHAR(97)` would return `a`, because the ASCII code 97 corresponds to the character `a`.
3. `=CHAR(32)` would return a space (` `), as the ASCII code 32 corresponds to the space character.
4. `=CHAR(48)` would return `0`, as the ASCII code 48 corresponds to the character `0`.
5. `=CHAR(128)` would return the character associated with the extended ASCII code 128.

### Notes:

- The `CHAR` function is often used for inserting special characters, creating formatted text, and generating character
  sequences in formulas.
- The range of valid inputs is constrained to numbers between 1 and 255. If you provide a value outside this range,
  Excel will return a `#VALUE!` error.
- It is case-sensitive when interpreting characters, as ASCII codes for uppercase and lowercase letters differ (e.g.,
  `A` is 65, while `a` is 97).
- For non-English locales, `CHAR` may return characters from the extended ASCII set specific to the system’s regional
  settings.