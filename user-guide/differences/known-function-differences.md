<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
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

The TEXT function supports common format strings but may not handle every custom format pattern that Excel accepts. Standard number, date, and currency formats work correctly.

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
- **Database functions** (DAVERAGE, DCOUNT, DSUM, etc.) -- these use Excel's database query syntax
- **Web functions** (WEBSERVICE, FILTERXML, ENCODEURL) -- these require external HTTP access
- **Microsoft 365 exclusive functions** (STOCKHISTORY, DETECTLANGUAGE, TRANSLATE) -- these require Microsoft cloud services

See the [Alphabetical Function List](../alphabetical-functions.md) for the complete list of supported functions.

---

## Reporting Differences

If you discover a calculation that produces different results between Codcel and Excel, the generated test documentation is the first place to check. It compares Codcel's output against the values in your Excel workbook for the specific inputs defined there.

For differences not covered in this documentation, please contact support or visit [codcel.io](https://codcel.io).