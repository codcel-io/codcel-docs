<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# ISNONTEXT Function

The `ISNONTEXT` function in Excel is used to **check whether a value is anything other than text**. It returns TRUE for numbers, logical values, dates, errors, and blank cells, and FALSE only when the value is a text string. It is the exact negation of [`ISTEXT`](./istext.md), and is most useful when the positive case you care about is "this is not text" — for example when validating that a field really holds a number before using it in a calculation.

## Key Features of `ISNONTEXT`:

- Returns `FALSE` only when the value genuinely is a text string.
- Returns `TRUE` for numbers, logical values, dates, times, and error values.
- Returns `TRUE` for a **blank cell**, since an empty cell contains no text.
- Returns `FALSE` for an **empty string** `""`, which is text of zero length — the one case where blank and empty-string differ.
- Applied to a range, it evaluates each cell individually and returns an array of results.

## Syntax:

```plaintext
ISNONTEXT(value)
```

- **value**: The value or expression you want to test. Typically a cell reference or formula result.

## How `ISNONTEXT` Works:

1. `ISNONTEXT` evaluates the provided value or expression.
2. If the result is a text string — including a zero-length one — it returns `FALSE`.
3. For every other data type — number, logical, date, time, error, or blank — it returns `TRUE`.

`ISNONTEXT(x)` is always the opposite of `ISTEXT(x)`; there is no value for which both return the same answer.

## Examples:

### 1. A Number:

If A1 contains `42`:
```excel
=ISNONTEXT(A1)
```

**Result:**
```
TRUE
```

### 2. A Text Value:

If A1 contains `"Hello"`:
```excel
=ISNONTEXT(A1)
```

**Result:**
```
FALSE
```

### 3. A Number Stored as Text:

If A1 contains the text `"42"` rather than the number:
```excel
=ISNONTEXT(A1)
```

**Result:**
```
FALSE (the value is text, however numeric it looks)
```

### 4. A Blank Cell:

If A1 is empty:
```excel
=ISNONTEXT(A1)
```

**Result:**
```
TRUE (an empty cell contains no text)
```

### 5. An Empty String:

```excel
=ISNONTEXT("")
```

**Result:**
```
FALSE (a zero-length string is still text)
```

### 6. A Logical Value:

```excel
=ISNONTEXT(TRUE)
```

**Result:**
```
TRUE (TRUE is a logical value, not text)
```

### 7. Validating a Numeric Entry:

```excel
=IF(ISNONTEXT(A1), A1 * 1.2, "Enter a number, not text")
```

**Result:**
```
Calculates only when A1 holds something other than text
```

### 8. Counting Non-Text Cells in a Range:

```excel
=SUMPRODUCT(--ISNONTEXT(A1:A10))
```

**Result:**
```
Returns the number of cells in A1:A10 that do not hold text
```

## Notes:

- `ISNONTEXT` is broader than "is a number". It returns `TRUE` for errors and blanks too, so it is not a substitute for [`ISNUMBER`](../mathematical-functions/is_number.md) when you need a value you can actually calculate with.
- The blank versus empty-string distinction is the one to watch: a blank cell gives `TRUE`, but a formula returning `""` gives `FALSE`.
- If the argument evaluates to an error, `ISNONTEXT` returns `TRUE` rather than propagating the error — an error is not text.
- `TYPE` returns `2` for exactly the values that `ISNONTEXT` returns `FALSE` for, so `ISNONTEXT(A1)` and `TYPE(A1)<>2` are equivalent.
- `ISNONTEXT` is part of the IS family of information functions ([`ISBLANK`](./isblank.md), [`ISERR`](./iserr.md), [`ISERROR`](./iserror.md), [`ISEVEN`](./iseven.md), [`ISLOGICAL`](./islogical.md), [`ISNA`](./isna.md), `ISNONTEXT`, [`ISNUMBER`](../mathematical-functions/is_number.md), [`ISODD`](./isodd.md), [`ISTEXT`](./istext.md), etc.).

## Applications:

- **Input Validation**: Reject text entries in a field that must hold a number or a date.
- **Data Cleaning**: Count how many cells in a column are already free of text contamination.
- **Type Auditing**: Pair with [`ISTEXT`](./istext.md) to partition a mixed column into two complete halves.
- **Defensive Formulas**: Guard arithmetic against text arguments that would otherwise raise an error.
- **Conditional Formatting**: Highlight rows where a supposedly numeric key arrived as text.

## Related Functions:

- **[ISTEXT](./istext.md)**: Returns TRUE if the value is text — the exact negation.
- **[ISNUMBER](../mathematical-functions/is_number.md)**: Returns TRUE only for numbers; narrower than `ISNONTEXT`, which also accepts errors and blanks.
- **[ISBLANK](./isblank.md)**: Returns TRUE if the cell is empty.
- **[ISERROR](./iserror.md)**: Returns TRUE if the value is any error.
- **[TYPE](./type.md)**: Returns a numeric code indicating the data type of a value — `2` for text.
- **[N](./n.md)**: Converts a value to a number — text becomes `0`.

> **Tip:** `ISNONTEXT` is not the same as "is a number", because it also returns `TRUE` for errors and blank cells. If your formula is about to do arithmetic on the value, reach for [`ISNUMBER`](../mathematical-functions/is_number.md) instead — it excludes the two cases that would still break the calculation.
