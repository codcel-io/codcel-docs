<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

### Syntax:

    DOLLAR(number, [decimals])

- **number**: The numeric value you want to format as text.
- **decimals**: (Optional) The number of digits to the right of the decimal point. If omitted, it defaults to 2.

### Description:

The `DOLLAR` function in Excel is used to convert a number to text in a currency format, using the formatting style "$
#,##0.00". It applies the currency symbol defined by your system's regional settings and allows you to specify the
number of decimal places.

This function is useful when you need to display numbers as properly formatted currency for better readability or
presentation purposes.

For example:

    DOLLAR(number, decimals) = formatted currency string

### Examples:

1. `=DOLLAR(1234.567, 2)` would return `"$1,234.57"`, formatting the number to two decimal places with a dollar sign.
2. `=DOLLAR(1234.567, 0)` would return `"$1,235"`, rounding the number to the nearest whole number.
3. `=DOLLAR(-567.89, 2)` would return `"-$567.89"`, formatting a negative number as currency.
4. `=DOLLAR(4321.987,-1)` would return `"$4,320"`, rounding the number to the nearest tens.
5. `=DOLLAR(1234.567)` would return `"$1,234.57"`, as the default value for `decimals` is 2.

### Notes:

- If the `decimals` argument is negative, the number is rounded to the left of the decimal point.
- If the `decimals` argument is greater than 0, the result will include the specified number of decimal places.
- Non-numeric data provided to the `number` argument will result in a `#VALUE!` error.
- The `DOLLAR` function does not perform actual currency conversions; it only formats the number as a string with the
  system's currency symbol.
- Formatting using `DOLLAR` does not change the underlying numerical value of the cell. It merely displays the formatted
  currency as text.

*** While running the command line: calc-to-web-cmd, options exist to set the decimal separator, thousands separator and currency symbol. 
For Portuguese formatting set the following:

  - Decimal separator: -d ","
  - Currency symbol: -c "€"
  - Thousands separator: -t " "