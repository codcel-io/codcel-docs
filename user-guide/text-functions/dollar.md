<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
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

### Locale

`DOLLAR` places the currency symbol the way the locale places it. The symbol
itself is yours to set; only its position, the spacing around it and the shape of
the negative form come from the locale.

| Locale | `=DOLLAR(1234.56)` |
|--------|--------------------|
| `en-US` | `$1,234.56` |
| `en-GB` | `£1,234.56` |
| `de-DE` | `1.234,56 €` |
| `fr-FR` | `1 234,56 €` |
| `pt-BR` | `R$ 1.234,56` |
| `de-CH` | `CHF 1'234.56` |

Note that German and French put the symbol **after** the amount, separated by a
non-breaking space. Set the whole set with one flag:

```bash
codcel -e model.xlsx -p my-project --locale de-DE
```

or set the pieces individually with `-d`, `-t` and `-c`. See
[CLI Reference](../cli.md#formatting) and
[Runtime Formatting](../runtime-formatting.md).