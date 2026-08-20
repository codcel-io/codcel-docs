<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# ISLOGICAL Function

The `ISLOGICAL` function in Excel is used to **check whether a value is a logical (Boolean) value**. It returns TRUE only when the value is `TRUE` or `FALSE`, and FALSE for everything else — numbers, text, dates, errors, and blank cells. This function is useful for validating that a cell genuinely holds a Boolean rather than a number or a piece of text that merely looks like one.

## Key Features of `ISLOGICAL`:

- Returns `TRUE` only for the logical values `TRUE` and `FALSE`.
- Returns `FALSE` for numbers, **including `1` and `0`**, even though those coerce to `TRUE`/`FALSE` in arithmetic contexts.
- Returns `FALSE` for the text strings `"TRUE"` and `"FALSE"` — text that reads like a Boolean is not a Boolean.
- Returns `FALSE` for blank cells, dates, times, and error values.
- Commonly used to validate inputs before feeding them into logical functions such as `AND`, `OR`, or `NOT`.

## Syntax:

```plaintext
ISLOGICAL(value)
```

- **value**: The value or expression you want to test. Typically a cell reference or formula result.

## How `ISLOGICAL` Works:

1. `ISLOGICAL` evaluates the provided value or expression.
2. If the result is the logical `TRUE` or the logical `FALSE`, it returns `TRUE`.
3. For every other data type — number, text, date, time, error, or blank — it returns `FALSE`.

Note that no type coercion happens. `ISLOGICAL` asks what the value *is*, not what it could be converted to.

## Examples:

### 1. A Logical Value:

If A1 contains `TRUE`:
```excel
=ISLOGICAL(A1)
```

**Result:**
```
TRUE
```

### 2. A Number:

If A1 contains `1`:
```excel
=ISLOGICAL(A1)
```

**Result:**
```
FALSE (1 coerces to TRUE in arithmetic, but it is a number, not a logical value)
```

### 3. Text That Looks Logical:

If A1 contains the text `"TRUE"`:
```excel
=ISLOGICAL(A1)
```

**Result:**
```
FALSE
```

### 4. A Logical Literal:

```excel
=ISLOGICAL(FALSE)
```

**Result:**
```
TRUE
```

### 5. The Result of a Comparison:

```excel
=ISLOGICAL(A1>10)
```

**Result:**
```
TRUE (a comparison always produces a logical value)
```

### 6. A Blank Cell:

If A1 is empty:
```excel
=ISLOGICAL(A1)
```

**Result:**
```
FALSE
```

### 7. Validating an Input Before Using It:

```excel
=IF(ISLOGICAL(A1), IF(A1, "Enabled", "Disabled"), "Please enter TRUE or FALSE")
```

**Result:**
```
Guides the user to supply a real Boolean rather than a 1/0 or the word "TRUE"
```

### 8. Counting Logical Cells in a Range:

```excel
=SUMPRODUCT(--ISLOGICAL(A1:A10))
```

**Result:**
```
Returns the number of cells in A1:A10 that hold a logical value
```

## Notes:

- `ISLOGICAL` distinguishes types, it does not convert them. `ISLOGICAL(1)` is `FALSE` even though `IF(1, ...)` treats `1` as `TRUE`.
- Comparison operators (`=`, `<>`, `>`, `<`, `>=`, `<=`) always produce logical values, so `ISLOGICAL` applied to a comparison is always `TRUE`.
- `ISLOGICAL` is part of the IS family of information functions ([`ISBLANK`](./isblank.md), [`ISERR`](./iserr.md), [`ISERROR`](./iserror.md), [`ISEVEN`](./iseven.md), `ISLOGICAL`, [`ISNA`](./isna.md), [`ISNONTEXT`](./isnontext.md), [`ISNUMBER`](../mathematical-functions/is_number.md), [`ISODD`](./isodd.md), [`ISTEXT`](./istext.md), etc.).
- `TYPE` returns `4` for exactly the values that `ISLOGICAL` returns `TRUE` for, so `ISLOGICAL(A1)` and `TYPE(A1)=4` are equivalent.
- When applied to a range, `ISLOGICAL` evaluates each cell individually and returns an array of results.

## Applications:

- **Input Validation**: Confirm that a configuration flag really is a Boolean before branching on it.
- **Data Cleaning**: Find cells where a Boolean was entered as the text `"TRUE"` or as `1`/`0` and needs normalising.
- **Type Auditing**: Combine with `ISNUMBER` and `ISTEXT` to classify every cell in a mixed-type column.
- **Conditional Formatting**: Highlight cells whose type does not match the expected schema.
- **Defensive Formulas**: Guard logical functions against arguments of the wrong type.

## Related Functions:

- **[TYPE](./type.md)**: Returns a numeric code indicating the data type of a value — `4` for logical values.
- **[ISBLANK](./isblank.md)**: Returns TRUE if the cell is empty.
- **[ISERROR](./iserror.md)**: Returns TRUE if the value is any error.
- **[ISNA](./isna.md)**: Returns TRUE only if the value is the `#N/A` error.
- **[ISNUMBER](../mathematical-functions/is_number.md)**: Returns TRUE if the value is a number.
- **[ISTEXT](./istext.md)**: Returns TRUE if the value is text.
- **[N](./n.md)**: Converts a value to a number — logical `TRUE` becomes `1` and `FALSE` becomes `0`.

> **Tip:** Spreadsheets often accumulate a mix of real Booleans, the numbers `1`/`0`, and the text `"TRUE"`/`"FALSE"` in the same column, because each of the three looks identical once formatted. `ISLOGICAL` is the quickest way to find the odd ones out before they cause a subtle logic bug downstream.
