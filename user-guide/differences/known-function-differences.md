<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Known Function Differences

Some Excel functions may produce slightly different results in Codcel. This page lists known differences beyond the general [rounding](./rounding.md) and [type conversion](./type-conversions.md) differences.

---

## Functions with Known Precision Differences

### FORECAST.ETS (Non-Seasonal)

Non-seasonal forecasting produces results that differ from Excel by approximately 0.1-0.2 for small datasets. See [FORECAST.ETS Precision](./forecast-ets.md) for details.

---

## Functions with Limitations

### TEXT

The TEXT function supports common format strings but may not handle every custom format pattern that Excel accepts. Standard number, date, and currency formats work correctly, including localized month and weekday names, locale number symbols, and `[$SYMBOL-LCID]` currency prefixes — see [TEXT](../text-functions/text.md).

Two known gaps remain:

- **Colour codes are parsed and discarded.** `[Red]#,##0.00` formats the number correctly but the colour has nowhere to go, since `TEXT` returns a string rather than a styled cell.
- **Grouping is always by three digits.** Locales that group by lakh — CLDR gives Hindi `#,##,##0.00` — are rendered with uniform three-digit groups.

### TOCOL / TOROW

The optional `ignore` argument filters blank values only. Codcel does not track error values as a filterable
category during reshaping, so:

| `ignore` | Excel | Codcel |
|---|---|---|
| `0` | Keep all values | Keep all values |
| `1` | Ignore blanks | Ignore blanks |
| `2` | Ignore errors | **Keeps all values** — behaves as `0` |
| `3` | Ignore blanks and errors | **Ignores blanks only** — behaves as `1` |

An out-of-range `ignore` value is also accepted silently and treated as `0`, where Excel returns `#VALUE!`.

**Workaround:** wrap the array in `IFERROR` to substitute or blank out errors before reshaping — for example
`=TOCOL(IFERROR(A1:C10, ""), 1)` removes both blanks and errors.

See [TOCOL](../lookup-and-reference-functions/tocol.md) and [TOROW](../lookup-and-reference-functions/torow.md).

---

## Non-Deterministic Functions

The following functions produce different results on every run and will cause generated tests to fail:

- **RAND** -- returns a random decimal between 0 and 1
- **RANDBETWEEN** -- returns a random integer within a range
- **RANDARRAY** -- returns an array of random numbers

These are not calculation errors — the functions are working correctly. However, since each run produces different output, the generated tests cannot match the expected values from Excel.

**Workaround:** Before importing your workbook, replace cells using these functions with static values (select the cells, copy, then paste as values). This freezes the output so tests can verify against a fixed result.

---

## Functions Not Supported

The following categories of Excel functions are not implemented:

- **Cube functions** (CUBEVALUE, CUBEMEMBER, etc.) -- these require a connection to an OLAP data source
- **Web functions** (WEBSERVICE, FILTERXML, ENCODEURL) -- these require external HTTP access
- **Microsoft 365 exclusive functions** (STOCKHISTORY, DETECTLANGUAGE, TRANSLATE) -- these require Microsoft cloud services

Database functions (DAVERAGE, DCOUNT, DSUM, etc.) **are** supported -- see [Database Functions](../database-functions.md).

See the [Alphabetical Function List](../alphabetical-functions.md) for the complete list of supported functions.

---

## Reporting Differences

If you discover a calculation that produces different results between Codcel and Excel, the generated test documentation is the first place to check. It compares Codcel's output against the values in your Excel workbook for the specific inputs defined there.

For differences not covered in this documentation, please contact support or visit [codcel.io](https://codcel.io).