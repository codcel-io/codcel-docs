<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Date Handling

Codcel replicates Excel's date system, including its historical quirks. Understanding these details helps ensure your date calculations produce the expected results.

---

## The Lotus 1-2-3 1900 Date Bug

Excel inherited a bug from Lotus 1-2-3 that treats 1900 as a leap year. In reality, 1900 was not a leap year (the next century-year that was a leap year is 2000). This means Excel's date serial number 60 corresponds to the non-existent date "29 February 1900".

It is worth being precise about what this does and does not affect, because the name suggests a bigger problem than it is:

- **Excel's serial-to-date mapping is correct for every real date.** Serial 45066 really is 20 May 2023, and Codcel agrees.
- The only genuine anomalies are **serial 60**, which denotes a day that never existed, and **day counts that span February 1900** — Excel says there are 60 days between 1 January 1900 and 1 March 1900, where the true answer is 59.

### The two settings

Codcel separates the convention used to *read* the workbook from the convention the *generated code* uses:

| Setting | Applies to | Default |
|---|---|---|
| `--workbook-lotus-1-2-3-1900-date-bug` | Decoding serials read out of the `.xlsx` | `true` |
| `--allow-lotus-1-2-3-1900-date-bug` | The generated project's own date arithmetic | follows the workbook setting |

The workbook setting should essentially always stay enabled: it is the only convention that agrees with Excel about which calendar day a stored serial denotes. Turning it off would make Codcel read your dates wrongly.

### Disabling the runtime setting does not make dates "more correct"

!!! warning "This does not do what it sounds like"

    Disabling `--allow-lotus-1-2-3-1900-date-bug` **re-bases the serial number system**. It does not correct dates — it moves **every date from 1 March 1900 onward one day later** relative to Excel.

    | Serial | Bug enabled (Excel) | Bug disabled |
    |---|---|---|
    | 59 | 28 February 1900 | 28 February 1900 |
    | 61 | 1 March 1900 | 2 March 1900 |
    | 45066 | 20 May 2023 | 21 May 2023 |

    Only disable this if the serial numbers your generated code receives come from somewhere other than Excel and follow a strict 1900 system.

### When the two settings disagree

If you set them to different values, Codcel emits warning **T29** at transpile time. Dates themselves are unaffected — they are carried as instants, not serials — but any output whose *value* is a date serial (`DAYS`, `DATEDIF`, or a date cell formatted as a plain number) will differ by one day from the value Excel cached, so the generated test for that output will fail.

---

## Date Serial Numbers

Excel uses serial numbers to represent dates:

| Serial Number | Date |
|--------------|------|
| 1 | 1 January 1900 |
| 59 | 28 February 1900 |
| 60 | 29 February 1900 (does not exist) |
| 61 | 1 March 1900 |
| 1462 | 1 January 1904 |
| 44927 | 1 January 2023 |

### Serial 60

`chrono`, which Codcel uses for date arithmetic, cannot represent 29 February 1900 because that day does not exist. Codcel therefore maps **serial 60 onto 28 February 1900**, the same day serial 59 maps to. The two serials are indistinguishable once converted, and converting back yields 59.

This only matters for workbooks that store a literal serial 60, which in practice means workbooks doing deliberate arithmetic across February 1900.

---

## The 1904 Date System

Excel supports a second epoch, originally the default on Mac Excel and still selectable per workbook (File → Options → Advanced → "Use 1904 date system"). It numbers **1 January 1904 as serial 0** and has no phantom leap day, sitting exactly **1462 days** below the 1900 system.

Codcel reads the workbook's `date1904` flag and **rebases every serial onto the 1900 system as the file is loaded**. A 1904 workbook and its 1900 equivalent therefore produce identical dates in the generated project.

This covers `T_` table sheets as well as calculation sheets. A table sheet is read twice — once into the model and once into the Parquet or CSV file your generated code queries at runtime — and both copies are rebased, so a date lookup against a table matches the same row either way. The `codcel-tests/date-1900.xlsx` and `codcel-tests/date-1904.xlsx` fixture pair exists to hold that property: the two files describe the same days in the two epochs and must load identically, tables included.

When a 1904 workbook is detected, Codcel emits informational message **L33** so the conversion is never silent.

### The epoch is not a runtime setting

Unlike the Lotus bug, the 1904 epoch is **not** something the generated code can be configured with. It is a fact about the source file, resolved once while reading it:

- There is no `use_1904` field on `ValueFormat` and no `CODCEL_*` environment variable for it.
- The generated project always works in the 1900 system, because that is the only convention its data is in.

This is deliberate. A runtime epoch switch has no correct setting — the serials a generated program holds are already in one system — so it could only ever shift every date by four years. Applying the epoch in exactly one place is what makes that impossible.

### Overriding detection

Use `--date-system` if a workbook's flag is wrong or missing. It steers the *loader*, so it changes how serials are read, not how the generated code behaves:

```bash
--date-system auto   # read the workbook's own flag (default)
--date-system 1900   # read serials as 1900, whatever the file says
--date-system 1904   # read serials as 1904, whatever the file says
```

### What is not rebased

Two categories are deliberately left alone.

**Time-only cells.** A serial below 1 is treated as a time of day rather than a date. In a 1904 workbook a genuine `1904-01-01 12:00` timestamp therefore reads as the bare time `12:00` — exactly how 1900 workbooks already treat their own sub-1 serials. Durations (`[hh]:mm:ss`) are elapsed time and are never shifted either.

**General-formatted date serials.** Rebasing needs to know a number *is* a date, which comes from the cell's number format. A cell holding a raw serial with General formatting is indistinguishable from any other number, so it is not rebased. This is the same type-inference limitation described for the Lotus bug above: if you keep raw date serials in unformatted cells in a 1904 workbook, format them as dates so Codcel can see what they are.

**ISO-8601 date cells** are a separate case rather than an exception. Some non-Excel writers, and `.ods` files, store a date as the text `2023-05-20` instead of as a serial. Codcel converts those to a 1900 serial as it reads them, and the epoch never enters into it: the cell already names a calendar day, so there is no epoch to rebase from. A cell Codcel cannot parse is skipped with message **L34**.

---

## See Also

- [Settings Reference](../settings.md#allow-lotus-1-2-3-1900-date-bug) -- the date settings
- [Runtime Formatting](../runtime-formatting.md) -- overriding date behaviour via environment variables
- [Rounding Differences](./rounding.md) -- other precision differences
