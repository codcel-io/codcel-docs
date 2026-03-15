<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Text Functions

This contains the list of text functions that are currently supported by Codcel.


## String Functions

## B

### [BAHTTEXT](./text-functions/bahttext.md)
Converts a number to Thai text with the suffix "Baht" (Thai Baht currency format).

- **Purpose:** Expresses numeric currency values as their written-out equivalent in the Thai language, following Thai Baht
  currency conventions.

- **Formula:** BAHTTEXT(number)
  - `number` is the numeric value you want to convert to Thai text, or a reference to a cell containing a number.

- **Example Usage:**
  - `=BAHTTEXT(100)` returns `"หนึ่งร้อยบาทถ้วน"` (one hundred Baht exactly).
  - `=BAHTTEXT(1234.50)` returns the Thai text representation of 1,234 Baht and 50 Satang.
  - `=BAHTTEXT(A1)` converts the numeric value in cell A1 to Thai Baht text.

## A

### [ASC](./text-functions/asc.md)
Converts full-width (double-byte) characters within a string to half-width (single-byte) characters. Commonly used for
text processing in languages like Japanese and Chinese.

- **Purpose:** Transforms text with full-width characters (used in East Asian languages) into half-width equivalents for
  compatibility and standardization.

- **Formula:** ASC(text)
  - `text` is the string to be converted from full-width to half-width characters.

- **Example Usage:**
  - `=ASC("Ｈｅｌｌｏ　Ｗｏｒｌｄ")` returns `"Hello World"` (converts full-width characters and spaces to half-width).
  - `=ASC("ＡＢＣ１２３")` returns `"ABC123"` (converts full-width alphanumeric characters to half-width).
  - `=ASC(A1)` performs the conversion on the string in cell `A1`.

### [ARRAYTOTEXT](./text-functions/array_to_text.md)
Converts an array of values into a single text string or a vertical array in a specific format.

- **Purpose:** Converts an array or range of values into a text format that can be easily read or processed.

- **Formula:** ARRAYTOTEXT(array, format)
  - `array` is the range or array of values to convert to text.
  - `format` is an optional parameter specifying the output format:
    - `0` (default): Produces a single text string with values separated by commas (horizontal array).
    - `1`: Produces a vertical array with values separated by line breaks.

- **Example Usage:**
  - `=ARRAYTOTEXT({1,2,3})` returns `"1,2,3"`.
  - `=ARRAYTOTEXT({1;2;3}, 1)` returns:
    ```
    1
    2
    3
    ```
  - `=ARRAYTOTEXT(A1:C1)` returns a comma-separated string of values in the range `A1:C1`.

## C

### [CONCATENATE](text-functions/concatenate.md)
Joins two or more text strings into one.

- **Example:** `=CONCATENATE("Hello", " ", "World!")`  
  **Result:** `Hello World!`

### [CONCAT](text-functions/concat.md)
Combines the text from multiple ranges and/or strings. Similar to `CONCATENATE` but supports ranges.

- **Example:** `=CONCAT(A1:A3)`  
  **Result:** Combines all text values from `A1` to `A3`.


### [CHAR](./text-functions/char.md)
Returns the character corresponding to a numeric code.

- **Purpose:** Converts a number into its corresponding character based on the Unicode character set.

- **Formula:** CHAR(number)
  - number is an integer from 1 to 255 (for Windows) or a valid Unicode value (on modern systems).

- **Example Usage:**
  - =CHAR(65) returns "A" (the character corresponding to Unicode value 65).
  - =CHAR(97) returns "a" (the character corresponding to Unicode value 97).

### [CODE](./text-functions/code.md)
Returns a numeric code for the first character in a text string, based on the character set used by your computer.

- **Purpose:** Retrieves the numeric (Unicode) value corresponding to the first character in a text string.

- **Formula:** CODE(text)
  - `text` is the input string or cell reference containing the text.
  - If the `text` is empty, CODE will return a `#VALUE!` error.

- **Example Usage:**
  - `=CODE("A")` returns `65` (the Unicode code for "A").
  - `=CODE("a")` returns `97` (the Unicode code for "a").
  - `=CODE("€")` returns `8364` (the Unicode code for "€").
  - `=CODE(A1)` returns the code for the first character in the text from cell A1.

### [CLEAN](./text-functions/clean.md)
Removes all non-printable characters from text.

- **Purpose:** Ensures text is free of characters that may cause issues in processing or display.

- **Formula:** CLEAN(text)
  - **text** is the input string or cell reference containing the text to clean.

- **Example Usage:**
  - =CLEAN("Hello	World") returns "HelloWorld" (removes the tab character).
  - =CLEAN(A1) removes non-printable characters from the text in cell A1.
  - =CLEAN("Line1Line2") returns "Line1Line2" (removes line breaks and other non-printable characters).

## D

### [DBCS](./text-functions/dbcs.md)
Converts half-width (single-byte) characters within a string to full-width (double-byte) characters. Commonly used for
text processing in languages like Japanese and Chinese.

- **Purpose:** Transforms text with half-width characters into full-width equivalents for compatibility and
  standardization in East Asian language contexts. Inverse of the `ASC` function.

- **Formula:** DBCS(text)
  - `text` is the string to be converted from half-width to full-width characters.

- **Example Usage:**
  - `=DBCS("Hello")` returns `"Ｈｅｌｌｏ"` (converts half-width characters to full-width).
  - `=DBCS("ABC123")` returns `"ＡＢＣ１２３"` (converts half-width alphanumeric characters to full-width).
  - `=DBCS(A1)` performs the conversion on the string in cell `A1`.

### [DOLLAR](./text-functions/dollar.md)
Formats a number as text using currency format.

- **Purpose:** Converts a number to a currency-formatted text string, rounded to a specified number of decimal places.

- **Formula:** DOLLAR(number, decimals)
  - `number` is the numeric value you want to format as currency.
  - `decimals` specifies the number of digits to the right of the decimal point. If omitted, defaults to 2.

- **Example Usage:**
  - `=DOLLAR(1234.567, 2)` returns "$1,234.57" (rounds to 2 decimal places).
  - `=DOLLAR(-1234.567, 0)` returns "$1,235" (rounds to the nearest integer and formats negative numbers with parentheses).
  - `=DOLLAR(1234.567, -1)` returns "$1,230" (rounds to the nearest 10).

## E

### [EXACT](./text-functions/exact.md)
Compares two text strings and returns `TRUE` if they are exactly the same, or `FALSE` otherwise. The comparison is
case-sensitive.

- **Purpose:** Checks whether two text strings are identical.

- **Formula:** EXACT(text1, text2)
  - `text1` and `text2` are the two strings to compare.

- **Example Usage:**
  - `=EXACT("Apple", "Apple")` returns `TRUE`.
  - `=EXACT("Apple", "apple")` returns `FALSE` (case-sensitive comparison).

## F

### [FIND](./text-functions/find.md)
Returns the position of a specific character or substring within a text string, case-sensitive. Allows for an optional starting position.

- **Example:** `=FIND("p", "Apple", 1)`
  **Result:** The position of the first occurrence of "p" in the string "Apple" (e.g., `2`).

### [FINDB](./text-functions/findb.md)
Returns the starting position of one text string within another, measured in bytes rather than characters. Case-sensitive.

- **Purpose:** Locates a substring within a text string and returns the byte position. In single-byte character set
  (SBCS) languages like English, `FINDB` behaves identically to `FIND`. In double-byte character set (DBCS) languages
  such as Japanese, Chinese, and Korean, each double-byte character is counted as 2 bytes.

- **Formula:** FINDB(find_text, within_text, [start_num])
  - `find_text` is the text you want to find.
  - `within_text` is the text in which to search.
  - `start_num` (optional) is the byte position at which to start the search. Defaults to 1.

- **Example Usage:**
  - `=FINDB("World", "Hello World")` returns `7` (byte position of "World" in an SBCS environment).
  - `=FINDB("cat", "Concatenation")` returns `4` (case-sensitive; "cat" starts at byte 4).
  - `=FINDB("Cat", "Concatenation")` returns `#VALUE!` (case-sensitive; uppercase "Cat" is not found).

### [FIXED](./text-functions/fixed.md)   
Rounds a number to a specified number of decimals and formats it as text. Optionally, you can remove commas.

- **Purpose:** Converts a number into text with a specified number of decimal points, formatted without scientific
  notation.

- **Formula:** FIXED(number, decimals, no_commas)
  - `number` is the numeric value you want to format.
  - `decimals` specifies the number of digits to the right of the decimal point. Defaults to 2 if omitted.
  - `no_commas` is a boolean (TRUE/FALSE) indicating whether to suppress commas in the formatted text. Defaults to
    `FALSE`.

- **Example Usage:**
  - `=FIXED(1234.567, 2)` returns `1,234.57`.
  - `=FIXED(1234.567, 2, TRUE)` returns `1234.57` (without commas).
  - `=FIXED(1234.567, -1)` returns `1,230` (rounded to the nearest 10 and includes commas).
  - `=FIXED(1234.567)` returns `1,234.57` (defaults to 2 decimals and includes commas).

## J

### [JIS](./text-functions/jis.md)
Converts half-width (single-byte) characters within a string to full-width (double-byte) characters. Equivalent to the
`DBCS` function, named after the Japanese Industrial Standard character encoding.

- **Purpose:** Transforms text with half-width characters into full-width equivalents for compatibility and
  standardization in East Asian language contexts. Inverse of the `ASC` function.

- **Formula:** JIS(text)
  - `text` is the string to be converted from half-width to full-width characters.

- **Example Usage:**
  - `=JIS("Hello")` returns `"Ｈｅｌｌｏ"` (converts half-width characters to full-width).
  - `=JIS("ABC123")` returns `"ＡＢＣ１２３"` (converts half-width alphanumeric characters to full-width).
  - `=JIS(A1)` performs the conversion on the string in cell `A1`.

## L

### [LEFT](./text-functions/left.md)
Returns the first specified number of characters from a text string.

- **Purpose:** Extracts a substring from the beginning of a given text string.

- **Formula:** `LEFT(text, num_chars)`
  - `text` is the string from which you want to extract characters.
  - `num_chars` specifies the number of characters to extract from the start. Defaults to 1 if omitted.

- **Example Usage:**
  - `=LEFT("Excel Functions", 5)` returns `"Excel"` (first 5 characters of the string).
  - `=LEFT("Excel", 3)` returns `"Exc"` (first 3 characters of the string).
  - `=LEFT(A1, 4)` extracts the first 4 characters from the text in cell A1.

### [LEFTB](./text-functions/leftb.md)
Returns the first character or characters in a text string, based on the number of bytes you specify rather than characters.

- **Purpose:** Extracts a substring from the beginning of a given text string measured in bytes. In single-byte character
  set (SBCS) languages like English, `LEFTB` behaves identically to `LEFT`. In double-byte character set (DBCS) languages
  such as Japanese, Chinese, and Korean, each double-byte character is counted as 2 bytes.

- **Formula:** LEFTB(text, [num_bytes])
  - `text` is the string from which you want to extract characters.
  - `num_bytes` (optional) specifies the number of bytes to extract from the start. Defaults to 1 if omitted.

- **Example Usage:**
  - `=LEFTB("Excel", 2)` returns `"Ex"` (first 2 bytes in an SBCS environment).
  - `=LEFTB("Excel")` returns `"E"` (defaults to 1 byte).
  - `=LEFTB(A1, 4)` extracts the first 4 bytes from the text in cell A1.

### [LEN](./text-functions/len.md)
Returns the number of characters in a text string, including spaces, punctuation, and numbers.

- **Purpose:** Counts every character in the specified text, useful for data validation, text processing, and measuring
  text length.

- **Formula:** LEN(text)
  - `text` is the text string, cell reference, or text value whose length you want to determine.

- **Example Usage:**
  - `=LEN("Hello World")` returns `11` (11 characters including the space).
  - `=LEN("Excel 365")` returns `9` (counts both letters and spaces).
  - `=LEN(A1)` returns the number of characters in the text from cell A1.

### [LENB](./text-functions/lenb.md)
Returns the number of bytes in a text string rather than the number of characters.

- **Purpose:** Measures the byte length of a text string. In single-byte character set (SBCS) languages like English,
  `LENB` behaves identically to `LEN`. In double-byte character set (DBCS) languages such as Japanese, Chinese, and
  Korean, each double-byte character is counted as 2 bytes.

- **Formula:** LENB(text)
  - `text` is the string whose byte length you want to determine.

- **Example Usage:**
  - `=LENB("Hello")` returns `5` (5 bytes in an SBCS environment).
  - `=LENB("")` returns `0` (an empty string contains 0 bytes).
  - `=LENB(A1)` returns the byte length of the text in cell A1.

### [LOWER](./text-functions/lower.md)
Converts all uppercase letters in a text string to lowercase.

- **Purpose:** Ensures a string is converted to all lowercase letters.

- **Formula:** LOWER(text)
  - `text` is the string or cell reference to be converted to lowercase.

- **Example Usage:**
  - `=LOWER("HELLO WORLD")` returns `hello world`.
  - `=LOWER(A1)` converts the text in cell A1 to lowercase.

## M

### [MID](./text-functions/mid.md)
Returns a specific number of characters from a text string, starting at the position you specify.

- **Purpose:** Extracts a substring from a text string based on a starting position and length.

- **Formula:** MID(text, start_num, num_chars)
  - `text` is the string containing the characters to extract.
  - `start_num` is the position (1-based) in the text string where the extraction begins.
  - `num_chars` specifies the number of characters to extract.

- **Example Usage:**
  - `=MID("Excel Functions", 1, 5)` returns `"Excel"` (extracts first 5 characters starting at position 1).
  - `=MID("Excel Functions", 7, 9)` returns `"Functions"` (extracts 9 characters starting at position 7).
  - `=MID(A1, 3, 4)` extracts 4 characters from the string in cell A1 starting at the 3rd character.

### [MIDB](./text-functions/midb.md)
Returns a specific number of characters from a text string, starting at the position you specify, based on the number of bytes rather than characters.

- **Purpose:** Extracts a substring from a text string measured in bytes. In single-byte character set (SBCS) languages
  like English, `MIDB` behaves identically to `MID`. In double-byte character set (DBCS) languages such as Japanese,
  Chinese, and Korean, each double-byte character is counted as 2 bytes.

- **Formula:** MIDB(text, start_num, num_bytes)
  - `text` is the string containing the characters to extract.
  - `start_num` is the byte position (1-based) in the text string where the extraction begins.
  - `num_bytes` specifies the number of bytes to extract.

- **Example Usage:**
  - `=MIDB("Excel Functions", 1, 5)` returns `"Excel"` (extracts first 5 bytes starting at byte 1 in an SBCS environment).
  - `=MIDB("Excel Functions", 7, 9)` returns `"Functions"` (extracts 9 bytes starting at byte 7 in an SBCS environment).
  - `=MIDB(A1, 3, 4)` extracts 4 bytes from the string in cell A1 starting at the 3rd byte.

## N

### [NUMBERVALUE](./text-functions/number_value.md)
Converts text to a number in a locale-independent manner.

- **Purpose:** Interprets a text value as a number, using specified decimal and grouping separators.

- **Formula:** NUMBERVALUE(text, [decimal_separator], [group_separator])
  - `text` is the text to convert into a number.
  - `decimal_separator` (optional) is the character used as the decimal point in the text. Defaults to `"."`.
  - `group_separator` (optional) is the character used as the grouping (thousands) separator in the text.

- **Example Usage:**
  - `=NUMBERVALUE("1,234.56", ".", ",")` returns `1234.56`.
  - `=NUMBERVALUE("1.234,56", ",", ".")` returns `1234.56`.
  - `=NUMBERVALUE("1234.56")` returns `1234.56` (uses defaults for separators).

## P

### [PROPER](./text-functions/proper.md)
Capitalizes the first letter of each word in a text string and converts the rest of the letters to lowercase.

- **Purpose:** Formats text to proper case, where the first letter of each word is uppercase, and all other letters are
  lowercase.

- **Formula:** `PROPER(text)`
  - `text` is the string or cell reference to transform into proper case.

- **Example Usage:**
  - `=PROPER("hello world")` returns `"Hello World"`.
  - `=PROPER("EXCEL functions")` returns `"Excel Functions"`.
  - `=PROPER(A1)` converts the text in cell A1 to proper case.

### [PHONETIC](./text-functions/phonetic.md)
Extracts the furigana (phonetic guide) characters from a text string in a cell.

- **Purpose:** Retrieves the phonetic reading (furigana) stored as metadata when Japanese text is entered via an Input
  Method Editor (IME). Useful for sorting, displaying pronunciation, or extracting reading data from kanji.

- **Formula:** PHONETIC(reference)
  - `reference` is a cell reference or range of cells containing text with furigana information.

- **Example Usage:**
  - `=PHONETIC(A1)` returns the katakana phonetic reading stored with the Japanese text in cell A1 (e.g., `トウキョウ` for `東京`).
  - `=PHONETIC(A1:A3)` concatenates the furigana readings from all cells in the range A1 through A3.
  - `=PHONETIC(B2)` if B2 contains `"Hello"` (no furigana data), returns `"Hello"` unchanged.

## R

### [REGEXEXTRACT](./text-functions/regexextract.md)
Extracts the first substring that matches a regular expression pattern from a text string.

- **Purpose:** Parses and extracts text matching a specified regular expression, returning the first match or first
  capture group. Useful for extracting numbers, emails, codes, or other patterns from free-form text.

- **Formula:** REGEXEXTRACT(text, regular_expression)
  - `text` is the input string from which to extract matching content.
  - `regular_expression` is the regex pattern to match. If the pattern contains capture groups, the first capture
    group's content is returned.

- **Example Usage:**
  - `=REGEXEXTRACT("Order #12345 placed", "[0-9]+")` returns `"12345"` (extracts the first sequence of digits).
  - `=REGEXEXTRACT("Email: user@example.com", "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}")` returns `"user@example.com"`.
  - `=REGEXEXTRACT("Invoice INV-2024-0987", "INV-(\d{4})-(\d+)")` returns `"2024"` (first capture group).

### [REGEXTEST](./text-functions/regextest.md)
Tests whether a text string matches a regular expression pattern, returning TRUE or FALSE.

- **Purpose:** Validates whether text conforms to a specified regular expression pattern. Useful for data validation,
  filtering, and conditional logic based on text patterns.

- **Formula:** REGEXTEST(text, regular_expression)
  - `text` is the input string to test against the pattern.
  - `regular_expression` is the regex pattern to match. Returns `TRUE` if the pattern is found anywhere in the text.

- **Example Usage:**
  - `=REGEXTEST("Order #12345 placed", "[0-9]+")` returns `TRUE` (the text contains digits).
  - `=REGEXTEST("Hello World", "^[A-Z]")` returns `TRUE` (the text starts with an uppercase letter).
  - `=REGEXTEST("No numbers here", "\d+")` returns `FALSE` (no digits found).

### [REGEXREPLACE](./text-functions/regexreplace.md)
Replaces all substrings that match a regular expression pattern within a text string with a replacement string.

- **Purpose:** Performs advanced find-and-replace operations using regular expressions, supporting capture group
  backreferences in the replacement string. Useful for reformatting, cleaning, and restructuring text patterns.

- **Formula:** REGEXREPLACE(text, regular_expression, replacement)
  - `text` is the input string in which to perform the replacement.
  - `regular_expression` is the regex pattern to match.
  - `replacement` is the text to substitute for each match. Can include backreferences (`$1`, `$2`, etc.) to capture
    groups.

- **Example Usage:**
  - `=REGEXREPLACE("Order #12345 placed", "[0-9]+", "XXXXX")` returns `"Order #XXXXX placed"`.
  - `=REGEXREPLACE("Hello   World", "\s+", " ")` returns `"Hello World"` (collapses multiple spaces).
  - `=REGEXREPLACE("2024-01-15", "(\d{4})-(\d{2})-(\d{2})", "$2/$3/$1")` returns `"01/15/2024"` (reformats date).

### [REPLACE](./text-functions/replace.md)
Replaces part of a text string with a new text string, based on a starting position and length.

- **Purpose:** Substitutes a portion of a text string with a different text string.

- **Formula:** REPLACE(old_text, start_num, num_chars, new_text)
  - `old_text` is the original text string.
  - `start_num` is the position in the text string where the replacement begins (1-based).
  - `num_chars` is the number of characters to replace.
  - `new_text` is the text string that replaces the specified portion of `old_text`.

- **Example Usage:**
  - `=REPLACE("Hello World", 7, 5, "Excel")` returns `"Hello Excel"` (replaces "World" with "Excel").
  - `=REPLACE("12345", 2, 3, "678")` returns `"16785"` (replaces "234" with "678").
  - `=REPLACE(A1, 1, 4, "Test")` replaces the first 4 characters of the text in cell A1 with the string "Test".

### [REPLACEB](./text-functions/replaceb.md)
Replaces part of a text string with a new text string, based on a starting byte position and number of bytes rather than characters.

- **Purpose:** Substitutes a portion of a text string with a different text string using byte positions, which is important for double-byte character set (DBCS) languages.

- **Formula:** REPLACEB(old_text, start_num, num_bytes, new_text)
  - `old_text` is the original text string.
  - `start_num` is the byte position in the text string where the replacement begins (1-based).
  - `num_bytes` is the number of bytes to replace.
  - `new_text` is the text string that replaces the specified bytes of `old_text`.

- **Example Usage:**
  - `=REPLACEB("HelloWorld", 6, 5, "Excel")` returns `"HelloExcel"` (replaces "World" with "Excel" by byte position).
  - `=REPLACEB("12345", 2, 3, "678")` returns `"16785"` (replaces 3 bytes starting at byte 2).
  - `=REPLACEB(A1, 1, 4, "Test")` replaces the first 4 bytes of text in cell A1 with the string "Test".

### [REPT](./text-functions/rept.md)
Repeats a text string a specified number of times.

- **Purpose:** Creates a new string by repeating an existing string a specified number of times.

- **Formula:** `REPT(text, number_times)`
  - `text` is the string to be repeated.
  - `number_times` specifies the number of times the text should be repeated.
    - If `number_times` is 0, an empty string (`""`) is returned.
    - If `number_times` is negative, an error is returned.

- **Example Usage:**
  - `=REPT("A", 3)` returns `"AAA"` (repeats "A" 3 times).
  - `=REPT("*", 5)` returns `"*****"` (repeats "*" 5 times).
  - `=REPT(A1, 2)` repeats the text in cell `A1` two times.
  - `=REPT("Hello ", 0)` returns `""` (empty string).

### [RIGHT](./text-functions/right.md)
Returns the last specified number of characters from a text string.

- **Purpose:** Extracts a substring from the end of a given text string.

- **Formula:** RIGHT(text, num_chars)
  - `text` is the string from which you want to extract characters.
  - `num_chars` specifies the number of characters to extract from the end. Defaults to 1 if omitted.

- **Example Usage:**
  - `=RIGHT("Excel Functions", 9)` returns `"Functions"` (last 9 characters of the string).
  - `=RIGHT("Excel", 3)` returns `"cel"` (last 3 characters of the string).
  - `=RIGHT(A1, 4)` extracts the last 4 characters from the text in cell A1.

### [RIGHTB](./text-functions/rightb.md)
Returns the last character or characters in a text string, based on the number of bytes you specify rather than characters.

- **Purpose:** Extracts a substring from the end of a given text string measured in bytes. In single-byte character
  set (SBCS) languages like English, `RIGHTB` behaves identically to `RIGHT`. In double-byte character set (DBCS) languages
  such as Japanese, Chinese, and Korean, each double-byte character is counted as 2 bytes.

- **Formula:** RIGHTB(text, [num_bytes])
  - `text` is the string from which you want to extract characters.
  - `num_bytes` (optional) specifies the number of bytes to extract from the end. Defaults to 1 if omitted.

- **Example Usage:**
  - `=RIGHTB("Excel", 3)` returns `"cel"` (last 3 bytes in an SBCS environment).
  - `=RIGHTB("Excel")` returns `"l"` (defaults to 1 byte).
  - `=RIGHTB(A1, 4)` extracts the last 4 bytes from the text in cell A1.

## S

### [SEARCH](./text-functions/search.md)
Returns the position of a specific character or substring within a text string, ignoring case. Allows for optional starting position.

- **Example:** `=SEARCH("a", "Apple", 1)`
  **Result:** The position of the first occurrence of "a" in the string "Apple" (e.g., `1`).

### [SEARCHB](./text-functions/searchb.md)
Returns the starting position of one text string within another, measured in bytes rather than characters. Case-insensitive.

- **Purpose:** Locates a substring within a text string and returns the byte position. In single-byte character set
  (SBCS) languages like English, `SEARCHB` behaves identically to `SEARCH`. In double-byte character set (DBCS) languages
  such as Japanese, Chinese, and Korean, each double-byte character is counted as 2 bytes.

- **Formula:** SEARCHB(find_text, within_text, [start_num])
  - `find_text` is the text you want to find. Wildcards `*` and `?` are supported.
  - `within_text` is the text in which to search.
  - `start_num` (optional) is the byte position at which to start the search. Defaults to 1.

- **Example Usage:**
  - `=SEARCHB("World", "Hello World")` returns `7` (byte position of "World" in an SBCS environment).
  - `=SEARCHB("cat", "Concatenation")` returns `4` (case-insensitive; "cat" starts at byte 4).
  - `=SEARCHB("CAT", "Concatenation")` returns `4` (case-insensitive; "CAT" matches "cat" at byte 4).

### [SUBSTITUTE](./text-functions/substitute.md)
Replaces occurrences of a specified substring within a text string with another substring.

- **Purpose:** Substitutes all occurrences of a substring within a text string with a new substring.

- **Formula:** SUBSTITUTE(text, old_text, new_text, [instance_num])
  - `text` is the original text string in which the substitution is to be performed.
  - `old_text` is the substring to be replaced.
  - `new_text` is the substring to replace `old_text`.
  - `instance_num` (optional) specifies which occurrence of `old_text` to replace. If omitted, all occurrences are
    replaced.

- **Example Usage:**
  - `=SUBSTITUTE("Hello World", "World", "Excel")` returns `"Hello Excel"` (replaces "World" with "Excel").
  - `=SUBSTITUTE("Banana", "a", "e")` returns `"Benene"` (replaces all occurrences of "a" with "e").
  - `=SUBSTITUTE("Mississippi", "s", "z", 2)` returns `"Mizzissippi"` (replaces the 2nd occurrence of "s" with "z").

## T

### [TEXT](./text-functions/text.md)
Converts a number or date into text in a specified format.

- **Purpose:** Formats a number or date and returns the result as text.

- **Formula:** TEXT(value, format_text)
  - `value` is the numeric value or date to format as text.
  - `format_text` is the format code specifying the desired formatting.

- **Example Usage:**
  - `=TEXT(1234.567, "0.00")` returns `"1234.57"` (formats the number with two decimal places).
  - `=TEXT(TODAY(), "DD/MM/YYYY")` returns `"25/10/2023"` (formats the current date as "DD/MM/YYYY").
  - `=TEXT(A1, "#,###")` formats the number in cell A1 with a thousands separator.

### [TEXTAFTER](./text-functions/text-after.md)   
Returns the text that occurs after a specific character or substring in a text string. Allows specifying the nth
occurrence.

- **Purpose:** Extracts a portion of text after a specified substring, with an optional occurrence parameter.

- **Formula:** TEXTAFTER(text, delimiter, [occurrence], [match_mode], [if_not_found])
  - `text` is the original text string.
  - `delimiter` specifies the character or substring after which text will be extracted.
  - `occurrence` (optional) specifies which occurrence of the delimiter should be used. Defaults to 1 (first
    occurrence). Negative values search for occurrences from the end of the text.
  - `match_mode` (optional) specifies case-sensitive matching (0 or omitted for case-sensitive, 1 for case-insensitive).
  - `if_not_found` (optional) is the value to return if the delimiter is not found. Defaults to an error if not
    provided.

- **Example Usage:**
  - `=TEXTAFTER("hello-world-excel", "-", 1)` returns `"world-excel"` (text after the first occurrence of `"-"`).
  - `=TEXTAFTER("hello-world-excel", "-", 2)` returns `"excel"` (text after the second occurrence of `"-"`).
  - `=TEXTAFTER("hello-world", "-", -1)` returns `"world"` (text after the last occurrence of `"-"`).
  - `=TEXTAFTER("hello-world", "|", 1, , "Not Found")` returns `"Not Found"` (delimiter not found, so returns the
    fallback value).
  - `=TEXTAFTER("HELLO-WORLD", "-", 1, 1)` returns `"WORLD"` (case-insensitive match).

### [TEXTBEFORE](./text-functions/text-before.md)
Returns the text that occurs before a specific character or substring in a text string. Allows specifying the nth
occurrence.

- **Purpose:** Extracts a portion of text before a specified substring, with an optional occurrence parameter.

- **Formula:** TEXTBEFORE(text, delimiter, [occurrence], [match_mode], [if_not_found])
  - `text` is the original text string.
  - `delimiter` specifies the character or substring before which text will be extracted.
  - `occurrence` (optional) specifies which occurrence of the delimiter should be used. Defaults to 1 (first
    occurrence). Negative values search for occurrences from the end of the text.
  - `match_mode` (optional) specifies case-sensitive matching (0 or omitted for case-sensitive, 1 for case-insensitive).
  - `if_not_found` (optional) is the value to return if the delimiter is not found. Defaults to an error if not
    provided.

- **Example Usage:**
  - `=TEXTBEFORE("hello-world-excel", "-", 1)` returns `"hello"` (text before the first occurrence of `"-"`).
  - `=TEXTBEFORE("hello-world-excel", "-", 2)` returns `"hello-world"` (text before the second occurrence of `"-"`).
  - `=TEXTBEFORE("hello-world", "-", -1)` returns `"hello"` (text before the last occurrence of `"-"`).
  - `=TEXTBEFORE("hello-world", "|", 1, , "Not Found")` returns `"Not Found"` (delimiter not found, so returns the
    fallback value).
  - `=TEXTBEFORE("HELLO-WORLD", "-", 1, 1)` returns `"HELLO"` (case-insensitive match).

### [TEXTSPLIT](./text-functions/text-split.md)
Splits text into an array based on specified row and/or column delimiters.

- **Purpose:** Extracts portions of a text string into separate cells or an array by using delimiters.

- **Formula:** TEXTSPLIT(text, column_delimiter, [row_delimiter])
  - `text` is the string to be split.
  - `column_delimiter` specifies the character(s) used to split the text into columns.
  - `row_delimiter` (optional) specifies the character(s) used to split the text into rows.

- **Example Usage:**
  - `=TEXTSPLIT("Apple,Banana,Cherry", ",")` returns an array of `{"Apple", "Banana", "Cherry"}` (split by a comma).
  - `=TEXTSPLIT("Row1|Row2|Row3", "|", ";")` splits the text first into rows using `"|"` and then into columns using
    `";"`.
  - `=TEXTSPLIT(A1, ",", ";")` splits the text in cell `A1` using both row and column delimiters.

### [TEXTJOIN](text-functions/text-join.md)
Combines text from multiple ranges and/or strings, using a delimiter. Allows the option to ignore empty cells.

- **Example:** `=TEXTJOIN(", ", TRUE, A1:A3)`  
  **Result:** Text values from `A1` to `A3`, separated by a comma (e.g., `Item1, Item2, Item3`).

### [TRIM](./text-functions/trim.md)
Removes all extra spaces from a text string, leaving only single spaces between words.

- **Purpose:** Cleans up text by removing extra spaces, while keeping single spaces between words.

- **Formula:** `TRIM(text)`
  - `text` is the string or cell reference from which to remove extra spaces.

- **Example Usage:**
  - `=TRIM("  Hello   World  ")` returns `"Hello World"` (removes leading, trailing, and extra spaces between words).
  - `=TRIM(A1)` removes extra spaces from the text in cell `A1`.

## U

### [UNICHAR](./text-functions/uni_char.md)
Returns the Unicode character that is referenced by the given numeric value.

- **Purpose:** Converts a numeric Unicode code into the corresponding character.

- **Formula:** `UNICHAR(number)`
  - `number` is the numeric code used to determine the Unicode character.
    - Must be a valid Unicode numeric value.

- **Example Usage:**
  - `=UNICHAR(65)` returns `"A"` (the Unicode character for 65).
  - `=UNICHAR(128512)` returns `"😀"` (the Unicode character for 128512).
  - `=UNICHAR(A1)` returns the Unicode character for the numeric value in cell A1.

### [UNICODE](./text-functions/unicode.md)
Returns the numeric Unicode code for the first character in a text string.

- **Purpose:** Converts the first character of a text string into its corresponding Unicode numeric value.

- **Formula:** `UNICODE(text)`
  - `text` is the string whose first character's Unicode value is to be determined.
    - If `text` is empty, an error is returned.

- **Example Usage:**
  - `=UNICODE("A")` returns `65` (the Unicode code for "A").
  - `=UNICODE("😀")` returns `128512` (the Unicode code for "😀").
  - `=UNICODE(A1)` returns the Unicode code for the first character of the text in cell A1.

### [UPPER](./text-functions/upper.md)
Converts all lowercase letters in a text string to uppercase.

- **Purpose:** Transforms text by converting all lowercase characters to uppercase characters.

- **Formula:** `UPPER(text)`
  - `text` is the string or cell reference to convert.
    - Non-text characters and capitalized letters are not affected.

- **Example Usage:**
  - `=UPPER("hello")` returns `"HELLO"` (converts all lowercase characters to uppercase).
  - `=UPPER("Hello World")` returns `"HELLO WORLD"` (preserves uppercase, converts lowercase).
  - `=UPPER(A1)` converts the text in cell `A1` to uppercase.

## V

### [VALUE](./text-functions/value.md)   
Converts a text string that represents a number, date, or time into a numeric value.

- **Purpose:** Transforms a text representation of a number, date, or time into its numeric equivalent.

- **Formula:** `VALUE(text)`
  - `text` is the string to convert into a numeric value.
    - If `text` is not a valid number, date, or time, an error is returned.

- **Example Usage:**
  - `=VALUE("123")` returns `123` (converts the text "123" into a number).
  - `=VALUE("10/25/2023")` converts the date string into its corresponding serial number.
  - `=VALUE(A1)` evaluates the text in cell `A1` and converts it into a number, if possible.

### [VALUETOTEXT](./text-functions/value-to-text.md)
Converts a value to text in a specific format.

- **Purpose:** Transforms any type of value (number, date, logical, or error) into a text string.

- **Formula:** `VALUETOTEXT(value, [format_option])`
  - `value` is the value or reference to be converted into text.
  - `format_option` (optional) specifies how the text should be formatted:
    - `0` (default): Converts the value to text without quotes for strings.
    - `1`: Converts the value to text and encloses strings in double quotes.

- **Example Usage:**
  - `=VALUETOTEXT(123)` returns `"123"` (converts the number to text).
  - `=VALUETOTEXT("Hello")` (with `format_option` omitted) returns `Hello` (string without quotes).
  - `=VALUETOTEXT("Hello", 1)` returns `"Hello"` (string enclosed in quotes).
  - `=VALUETOTEXT(TRUE)` returns `"TRUE"` (logical value converted to text).
  - `=VALUETOTEXT(A1, 1)` converts the value in cell `A1` to text, preserving format as per the option.