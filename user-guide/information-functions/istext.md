<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# ISTEXT Function

The `ISTEXT` function in Excel is used to **check whether a value is text**. It returns TRUE when the value is a text string and FALSE for numbers, logical values, dates, errors, and blank cells. This function is useful for auditing columns that should hold one data type, for catching numbers that were imported as text, and for guarding text functions against arguments they cannot process.

## Key Features of `ISTEXT`:

- Returns `TRUE` only when the value genuinely is a text string.
- Returns `FALSE` for numbers, **including numbers formatted to look like text**, and for logical values, dates, times, and errors.
- Returns `TRUE` for an **empty string** `""`, which is text of zero length — this is not the same as a blank cell.
- Returns `FALSE` for a truly blank cell, where [`ISBLANK`](./isblank.md) returns `TRUE`.
- Applied to a range, it evaluates each cell individually and returns an array of results.

## Syntax:

```plaintext
ISTEXT(value)
```

- **value**: The value or expression you want to test. Typically a cell reference or formula result.

## How `ISTEXT` Works:

1. `ISTEXT` evaluates the provided value or expression.
2. If the result is a text string — including a zero-length one — it returns `TRUE`.
3. For every other data type — number, logical, date, time, error, or blank — it returns `FALSE`.

No type coercion happens. `ISTEXT` asks what the value *is*, not what it could be converted to, which is exactly what makes it useful for finding numbers stored as text.

## Examples:

### 1. A Text Value:

If A1 contains `"Hello"`:
```excel
=ISTEXT(A1)
```

**Result:**
```
TRUE
```

### 2. A Number:

If A1 contains `42`:
```excel
=ISTEXT(A1)
```

**Result:**
```
FALSE
```

### 3. A Number Stored as Text:

If A1 contains the text `"42"` rather than the number:
```excel
=ISTEXT(A1)
```

**Result:**
```
TRUE (this is how you find numbers that were imported as text)
```

### 4. An Empty String:

```excel
=ISTEXT("")
```

**Result:**
```
TRUE (a zero-length string is still text)
```

### 5. A Blank Cell:

If A1 is empty:
```excel
=ISTEXT(A1)
```

**Result:**
```
FALSE (an empty cell holds no value at all, so ISBLANK is TRUE here instead)
```

### 6. A Logical Value:

```excel
=ISTEXT(TRUE)
```

**Result:**
```
FALSE (TRUE is a logical value, not the text "TRUE")
```

### 7. Guarding a Calculation:

```excel
=IF(ISTEXT(A1), "Enter a number", A1 * 1.2)
```

**Result:**
```
Prompts for correct input instead of failing when A1 holds text
```

### 8. Counting Text Cells in a Range:

```excel
=SUMPRODUCT(--ISTEXT(A1:A10))
```

**Result:**
```
Returns the number of cells in A1:A10 that hold text
```

## Notes:

- `ISTEXT` distinguishes types, it does not convert them. `ISTEXT("42")` is `TRUE` even though `"42"*1` evaluates to `42`.
- The empty string is the main point of confusion: `ISTEXT("")` is `TRUE` while `ISTEXT(<empty cell>)` is `FALSE`. A formula returning `""` therefore produces a cell that `ISTEXT` calls text and [`ISBLANK`](./isblank.md) calls non-blank.
- If the argument evaluates to an error, `ISTEXT` returns `FALSE` rather than propagating the error, so `ISTEXT(FIND("x",A1))` is safe to use directly.
- `ISNONTEXT` is the exact negation of `ISTEXT` — it returns `TRUE` for everything `ISTEXT` returns `FALSE` for, blank cells included.
- `TYPE` returns `2` for exactly the values that `ISTEXT` returns `TRUE` for, so `ISTEXT(A1)` and `TYPE(A1)=2` are equivalent.
- `ISTEXT` is part of the IS family of information functions ([`ISBLANK`](./isblank.md), [`ISERR`](./iserr.md), [`ISERROR`](./iserror.md), [`ISEVEN`](./iseven.md), [`ISLOGICAL`](./islogical.md), [`ISNA`](./isna.md), [`ISNONTEXT`](./isnontext.md), [`ISNUMBER`](../mathematical-functions/is_number.md), [`ISODD`](./isodd.md), `ISTEXT`, etc.).

## Applications:

- **Import Auditing**: Find numeric columns where some values arrived as text and will not sum correctly.
- **Data Cleaning**: Flag cells needing conversion before a `VLOOKUP` fails on a type mismatch.
- **Input Validation**: Confirm that a name or code field really holds text before concatenating it.
- **Type Auditing**: Combine with [`ISNUMBER`](../mathematical-functions/is_number.md) and [`ISLOGICAL`](./islogical.md) to classify every cell in a mixed-type column.
- **Conditional Formatting**: Highlight cells whose type does not match the expected schema.

## Related Functions:

- **[ISNONTEXT](./isnontext.md)**: Returns TRUE if the value is anything other than text — the exact negation.
- **[ISNUMBER](../mathematical-functions/is_number.md)**: Returns TRUE if the value is a number.
- **[ISBLANK](./isblank.md)**: Returns TRUE if the cell is empty.
- **[ISLOGICAL](./islogical.md)**: Returns TRUE if the value is a logical value.
- **[TYPE](./type.md)**: Returns a numeric code indicating the data type of a value — `2` for text.
- **[N](./n.md)**: Converts a value to a number — text becomes `0`.

> **Tip:** A column that will not sum is almost always a `ISTEXT` problem. Drop `=SUMPRODUCT(--ISTEXT(A1:A1000))` next to it: if the count is anything but zero, some of those "numbers" are text and need converting before any arithmetic will see them.
