<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Date Handling

Codcel replicates Excel's date system, including its historical quirks. Understanding these details helps ensure your date calculations produce the expected results.

---

## The Lotus 1-2-3 1900 Date Bug

Excel inherited a bug from Lotus 1-2-3 that treats 1900 as a leap year. In reality, 1900 was not a leap year (the next century-year that was a leap year is 2000). This means Excel's date serial number 60 corresponds to the non-existent date "29 February 1900".

### How Codcel Handles This

By default, Codcel replicates this bug to ensure date serial numbers match Excel exactly. This is controlled by the **Allow Lotus 1-2-3 1900 Date Bug** setting (default: enabled).

- **Enabled (default):** Date serial numbers match Excel exactly, including the phantom 29 Feb 1900
- **Disabled:** Date serial numbers are astronomically correct, but may differ from Excel for dates before 1 March 1900

### When to Disable

Only disable this setting if:

- Your spreadsheet does not use date serial numbers
- You need astronomically correct dates before 1 March 1900
- You do not compare results against Excel

For most use cases, leave this setting enabled.

---

## Date Serial Numbers

Excel uses serial numbers to represent dates:

| Serial Number | Date |
|--------------|------|
| 1 | 1 January 1900 |
| 59 | 28 February 1900 |
| 60 | 29 February 1900 (does not exist) |
| 61 | 1 March 1900 |
| 44927 | 1 January 2023 |

All dates from 1 March 1900 onward are off by one serial number compared to the astronomical calendar due to the bug above. Codcel matches Excel's numbering.

---

## See Also

- [Settings Reference](../settings.md#allow-lotus-1-2-3-1900-date-bug) -- the date bug setting
- [Rounding Differences](./rounding.md) -- other precision differences