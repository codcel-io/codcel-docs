<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## DECIMAL Function

The `DECIMAL` function in Excel is used to convert a text representation of a number in a given base (radix) into its
decimal equivalent. This function is particularly useful when working with numbers in different numeral systems, such as
binary, octal, hexadecimal, etc.

### Syntax:

    DECIMAL(text, radix)

- **text**: This is a required argument. It specifies the text value representing the number in the given base.
- **radix**: This is a required argument. It specifies the base of the number system for the `text` value. It can be any
  integer between 2 and 36.

### Key Points:

- The `text` argument can contain digits, uppercase letters (A-Z), and lowercase letters (a-z) as valid characters,
  depending on the base.
    - For example, in base 16 (hexadecimal), valid characters include 0-9 and A-F.
- If the `radix` is not within the supported range of 2 to 36, Excel will return a `#NUM!` error.
- If the `text` contains invalid characters for the specified `radix`, Excel will return a `#VALUE!` error.

### Examples:

1. `=DECIMAL("1011", 2)`  
   Converts the binary number "1011" to its decimal equivalent.  
   **Result**: `11`

2. `=DECIMAL("1A", 16)`  
   Converts the hexadecimal number "1A" to its decimal equivalent.  
   **Result**: `26`

3. `=DECIMAL("77", 8)`  
   Converts the octal number "77" to its decimal equivalent.  
   **Result**: `63`

4. `=DECIMAL("Z", 36)`  
   Converts the base-36 number "Z" (representing the highest single digit in base-36) to its decimal equivalent.  
   **Result**: `35`

### Notes:

- The function is case-insensitive. For example, "A" and "a" in base 16 are treated the same.
- Ensure that the `text` strictly represents a valid number in the specified base. Adding invalid characters will cause
  an error.
- Use this function when dealing with numeral conversions between different bases and the decimal system.

> **Tip**: The `DECIMAL` function is a simple and efficient way to handle numeral system conversions directly in Excel.
It is particularly handy for working with binary, octal, or hexadecimal numbers in computing and engineering
applications.