<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# ISNA Function

The `ISNA` function in Excel is used to **check whether a value is the `#N/A` error specifically**. It returns TRUE when the value is `#N/A`, and FALSE for all other error types and all non-error values. `ISNA` is the natural companion to lookup functions like `VLOOKUP`, `XLOOKUP`, and `MATCH`, which use `#N/A` to signal "not found" — letting you distinguish a missing match from a genuine formula error.

## Key Features of `ISNA`:

- Returns `TRUE` only when the value is the `#N/A` error.
- Returns `FALSE` for all other error types (`#VALUE!`, `#REF!`, `#DIV/0!`, `#NUM!`, `#NAME?`, `#NULL!`).
- Returns `FALSE` for all non-error values — numbers, text, logicals, dates, and blanks.
- Pairs naturally with lookup functions (`VLOOKUP`, `XLOOKUP`, `MATCH`, `INDEX/MATCH`) to detect failed matches.
- Complements `ISERR`, which returns TRUE for all errors *except* `#N/A`.

## Syntax:

```plaintext
ISNA(value)
```

- **value**: The value or expression you want to test for the `#N/A` error. Typically a cell reference or formula result.

## How `ISNA` Works:

1. `ISNA` evaluates the provided value or expression.
2. If the result is the `#N/A` error, it returns `TRUE`.
3. If the result is any other error (`#VALUE!`, `#REF!`, `#DIV/0!`, `#NUM!`, `#NAME?`, `#NULL!`), it returns `FALSE`.
4. If the result is any non-error value, it returns `FALSE`.

## Examples:

### 1. Direct #N/A:

```excel
=ISNA(NA())
```

**Result:**
```
TRUE
```

### 2. Other Errors Are Not Detected:

If A1 contains `#DIV/0!`:
```excel
=ISNA(A1)
```

**Result:**
```
FALSE (ISNA only detects #N/A — use ISERROR for all errors)
```

### 3. Valid Number:

If A1 contains `100`:
```excel
=ISNA(A1)
```

**Result:**
```
FALSE
```

### 4. Failed VLOOKUP:

If "Unknown" is not present in the lookup range:
```excel
=ISNA(VLOOKUP("Unknown", A1:B10, 2, FALSE))
```

**Result:**
```
TRUE
```

### 5. Custom Message for Missing Lookups:

```excel
=IF(ISNA(VLOOKUP(A1, D:E, 2, FALSE)), "Not found", VLOOKUP(A1, D:E, 2, FALSE))
```

**Result:**
```
Returns "Not found" only when the lookup fails, propagates other errors as-is
```

### 6. Counting #N/A Cells in a Range:

```excel
=SUMPRODUCT(--ISNA(A1:A10))
```

**Result:**
```
Returns the number of cells in A1:A10 that contain #N/A
```

### 7. Separating #N/A from Other Errors:

```excel
=IF(ISNA(A1), "Missing", IF(ISERROR(A1), "Formula error", A1))
```

**Result:**
```
"Missing" for #N/A, "Formula error" for any other error, the value otherwise
```

### 8. Pairing with MATCH:

```excel
=IF(ISNA(MATCH("Apple", A1:A20, 0)), "Not in list", "Found at row " & MATCH("Apple", A1:A20, 0))
```

**Result:**
```
Reports whether "Apple" appears in the list and at which row
```

## Notes:

- `ISNA` is the narrowest of the error-detection functions: it matches one specific error, not the whole family.
- In modern Excel, `IFNA` is usually preferred over `IF(ISNA(...), ...)` for handling lookup failures — it's shorter and evaluates the lookup only once.
- `ISNA` returns `FALSE` for `#DIV/0!`, `#VALUE!`, and other errors. Use `ISERROR` if you want to catch every error type, or `ISERR` to catch every error *except* `#N/A`.
- `ISNA` is part of the IS family of information functions (`ISBLANK`, `ISERR`, `ISERROR`, `ISNA`, `ISNUMBER`, `ISTEXT`, [`ISLOGICAL`](./islogical.md), etc.).
- When applied to an array or range, `ISNA` evaluates each element and returns a corresponding array of TRUE/FALSE values.

## Applications:

- **Lookup Failure Handling**: Detect when `VLOOKUP`, `XLOOKUP`, `MATCH`, or `HLOOKUP` returned no match, so you can substitute a meaningful default.
- **Data Quality Checks**: Find cells deliberately marked with `=NA()` to indicate intentionally missing data.
- **Conditional Formatting**: Highlight cells with `#N/A` separately from cells with formula errors.
- **Layered Error Logic**: Combine with `ISERR` to branch on "not found" vs. "formula broke" cases.
- **Lookup Diagnostics**: Count or report missing keys in a lookup column when reconciling datasets.

## Related Functions:

- **[ISERROR](./iserror.md)**: Returns TRUE for any error, including `#N/A`.
- **[ISERR](./iserr.md)**: Returns TRUE for any error *except* `#N/A` — the complement of `ISNA`.
- **[ERROR.TYPE](./error_type.md)**: Returns a numeric code identifying which specific error a value is (1=`#NULL!`, …, 7=`#N/A`).
- **[NA](./na.md)**: Returns the `#N/A` error explicitly.
- **[IFNA](../logical-functions/ifna.md)**: Shorthand for `IF(ISNA(x), fallback, x)`.
- **[IFERROR](../conditional-functions/if_error.md)**: Returns a fallback value if a formula evaluates to any error.
- **[TYPE](./type.md)**: Returns a numeric code indicating the broad data type of a value (16 for any error).

> **Tip:** When working with lookups, prefer `IFNA(VLOOKUP(...), "Not found")` over `IF(ISNA(VLOOKUP(...)), "Not found", VLOOKUP(...))` — it's shorter, evaluates the lookup once, and makes intent clearer. Reserve `ISNA` for situations where you need the TRUE/FALSE result itself (e.g., counting missing matches with `SUMPRODUCT`, or branching on whether a key was found before doing further work).
