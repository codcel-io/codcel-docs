<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    BAHTTEXT(number)

- **number**: The numeric value you want to convert to Thai text, or a reference to a cell containing a number.

### Description:

The `BAHTTEXT` function in Excel converts a number to Thai text and adds the suffix "Baht". It is used to express
numeric currency values as their written-out equivalent in the Thai language, following Thai Baht currency conventions.

This function is primarily useful for financial documents, invoices, and receipts in Thailand where amounts must be
written out in words in Thai script.

For example:

    BAHTTEXT(number) = Thai text representation of the number with "บาท" (Baht) suffix

### Examples:

1. `=BAHTTEXT(1234.50)` would return the Thai text representation of 1,234 Baht and 50 Satang.
2. `=BAHTTEXT(100)` would return `"หนึ่งร้อยบาทถ้วน"`, representing "one hundred Baht exactly".
3. `=BAHTTEXT(0)` would return `"ศูนย์บาทถ้วน"`, representing "zero Baht exactly".
4. `=BAHTTEXT(A1)` converts the numeric value in cell A1 to Thai Baht text.
5. `=BAHTTEXT(67.75)` would return the Thai text for 67 Baht and 75 Satang.

### Notes:

- The `BAHTTEXT` function always returns a text string in Thai characters, regardless of the system language or locale.
- The result includes the Thai word for "Baht" (บาท) and, when there is no fractional part, the word "exactly" (ถ้วน).
- Fractional values are expressed in Satang (สตางค์), which is 1/100 of a Baht.
- Non-numeric data provided to the `number` argument will result in a `#VALUE!` error.
- Negative numbers are converted to Thai text with a leading negative indicator.
- The function is specifically designed for the Thai Baht currency and cannot be used for other currencies or languages.
- The output is a text string and cannot be used directly in mathematical calculations.