<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    ROMAN(number, [form])

- **number**: The Arabic number you want to convert to Roman numerals. It must be a positive integer between 1 and 3999.
- **form** *(optional)*: A number between 0 and 4 that specifies the type of Roman numeral formatting.
    - `0` or omitted: Classic Roman numerals (e.g., IV for 4, IX for 9).
    - `1` to `4`: Progressive simplification of the numeral format.
        - `1`: More concise form (less traditional).
        - `4`: Most simplified form.

### Examples:

1. `=ROMAN(1999)` would return `MCMXCIX` because 1999 in Roman numerals is MCMXCIX.

2. `=ROMAN(4)` would return `IV` because 4 in Roman numerals is IV.

3. `=ROMAN(4, 1)` would return `IIII` as a simplified form of Roman numerals for 4.

4. `=ROMAN(2024, 0)` would return `MMXXIV` because 2024 in Roman numerals is MMXXIV.

5. `=ROMAN(499, 4)` would return `ID` as the most simplified representation of 499.

> **Note**: If the input number is outside the valid range (1 to 3999), the `ROMAN` function will return a `#VALUE!` error.