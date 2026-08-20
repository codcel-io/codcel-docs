<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# ISEVEN Function

The `ISEVEN` function in Excel is used to **check whether a number is even**. It returns TRUE when the number divides exactly by two and FALSE when it does not. Decimal values are truncated toward zero before the test, so `ISEVEN` reports on the integer part of the number rather than rejecting fractional input. This function is useful for alternating row logic, splitting records into two groups, and validating that a count or identifier has the expected parity.

## Key Features of `ISEVEN`:

- Returns `TRUE` when the number is even and `FALSE` when it is odd.
- Truncates decimals **toward zero** before testing, so `ISEVEN(2.5)` returns `TRUE` because the integer part is `2`.
- Treats `0` as even, so `ISEVEN(0)` returns `TRUE`.
- Handles negative numbers by parity of the truncated value — `ISEVEN(-4)` returns `TRUE`.
- Is the exact complement of [`ISODD`](./isodd.md) for every value both functions accept.

## Syntax:

```plaintext
ISEVEN(number)
```

- **number**: The value you want to test for evenness. Typically a cell reference, a literal number, or a formula result.

## How `ISEVEN` Works:

1. `ISEVEN` converts the supplied value to a number.
2. The number is truncated toward zero, discarding any fractional part.
3. If the truncated value divides exactly by two, `ISEVEN` returns `TRUE`; otherwise it returns `FALSE`.

Truncation happens before the parity test, not after, which is why `ISEVEN(2.9)` and `ISEVEN(2)` give the same answer.

## Examples:

### 1. An Even Integer:

```excel
=ISEVEN(4)
```

**Result:**
```
TRUE
```

### 2. An Odd Integer:

```excel
=ISEVEN(7)
```

**Result:**
```
FALSE
```

### 3. Zero:

```excel
=ISEVEN(0)
```

**Result:**
```
TRUE (zero divides exactly by two)
```

### 4. A Decimal Value:

```excel
=ISEVEN(2.5)
```

**Result:**
```
TRUE (2.5 is truncated to 2 before the parity test)
```

### 5. A Negative Number:

```excel
=ISEVEN(-4)
```

**Result:**
```
TRUE
```

### 6. A Small Negative Decimal:

```excel
=ISEVEN(-0.9)
```

**Result:**
```
TRUE (truncation toward zero gives 0, which is even)
```

### 7. Banding Alternate Rows:

```excel
=IF(ISEVEN(ROW()), "Shaded", "Plain")
```

**Result:**
```
Alternates between "Shaded" and "Plain" down the column
```

### 8. Splitting Records Into Two Groups:

```excel
=IF(ISEVEN(A1), "Group A", "Group B")
```

**Result:**
```
Assigns each record to one of two groups based on the parity of its identifier
```

## Notes:

- `ISEVEN` truncates rather than rounds. `ISEVEN(3.9)` is `FALSE` because the integer part is `3`, even though `3.9` rounds to `4`.
- `ISEVEN` is a scalar function. Unlike [`ISTEXT`](./istext.md) or [`ISBLANK`](./isblank.md), it evaluates a single value rather than mapping across a range.
- A value that cannot be converted to a number produces an error rather than `FALSE`. Guard uncertain input with [`ISNUMBER`](../mathematical-functions/is_number.md) first.
- `#N/A` and infinite values are rejected as invalid numeric input.
- `ISEVEN` is part of the IS family of information functions ([`ISBLANK`](./isblank.md), [`ISERR`](./iserr.md), [`ISERROR`](./iserror.md), `ISEVEN`, [`ISLOGICAL`](./islogical.md), [`ISNA`](./isna.md), [`ISNONTEXT`](./isnontext.md), [`ISNUMBER`](../mathematical-functions/is_number.md), [`ISODD`](./isodd.md), [`ISTEXT`](./istext.md), etc.).

## Applications:

- **Alternating Row Formatting**: Combine with `ROW()` to band a table without a helper column.
- **Batch Assignment**: Split invoices, orders, or users into two balanced groups by identifier parity.
- **Data Validation**: Confirm that a quantity that must come in pairs really is even before processing.
- **Scheduling**: Drive fortnightly or every-other-period logic from a week or period number.
- **Checksum Logic**: Implement parity checks in identifier validation routines.

## Related Functions:

- **[ISODD](./isodd.md)**: Returns TRUE if the number is odd — the exact complement of `ISEVEN`.
- **[ISNUMBER](../mathematical-functions/is_number.md)**: Returns TRUE if the value is a number; useful as a guard before `ISEVEN`.
- **[EVEN](../mathematical-functions/even.md)**: Rounds a number up to the nearest even integer, rather than testing it.
- **[MOD](../mathematical-functions/mod.md)**: Returns the remainder of a division — `MOD(A1,2)=0` is the manual equivalent of `ISEVEN(A1)`.
- **[TYPE](./type.md)**: Returns a numeric code indicating the data type of a value.
- **[N](./n.md)**: Converts a value to a number — logical `TRUE` becomes `1` and `FALSE` becomes `0`.

> **Tip:** `ISEVEN` truncates toward zero rather than rounding, which is easy to forget when the input is a calculated value rather than a whole number. If the fractional part is meaningful to your test, wrap the argument in `ROUND` or `INT` explicitly so the parity you get is the parity you meant.
