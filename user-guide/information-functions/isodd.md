<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# ISODD Function

The `ISODD` function in Excel is used to **check whether a number is odd**. It returns TRUE when the number leaves a remainder of one after division by two and FALSE when it divides exactly. Decimal values are truncated toward zero before the test, so `ISODD` reports on the integer part of the number rather than rejecting fractional input. This function is useful for alternating logic, splitting records into two groups, and validating the parity of a count or identifier.

## Key Features of `ISODD`:

- Returns `TRUE` when the number is odd and `FALSE` when it is even.
- Truncates decimals **toward zero** before testing, so `ISODD(3.7)` returns `TRUE` because the integer part is `3`.
- Treats `0` as even, so `ISODD(0)` returns `FALSE`.
- Handles negative numbers by parity of the truncated value — `ISODD(-5)` returns `TRUE`.
- Is the exact complement of [`ISEVEN`](./iseven.md) for every value both functions accept.

## Syntax:

```plaintext
ISODD(number)
```

- **number**: The value you want to test for oddness. Typically a cell reference, a literal number, or a formula result.

## How `ISODD` Works:

1. `ISODD` converts the supplied value to a number.
2. The number is truncated toward zero, discarding any fractional part.
3. If the truncated value leaves a remainder when divided by two, `ISODD` returns `TRUE`; otherwise it returns `FALSE`.

Truncation happens before the parity test, not after, which is why `ISODD(3.1)` and `ISODD(3)` give the same answer.

## Examples:

### 1. An Odd Integer:

```excel
=ISODD(7)
```

**Result:**
```
TRUE
```

### 2. An Even Integer:

```excel
=ISODD(4)
```

**Result:**
```
FALSE
```

### 3. Zero:

```excel
=ISODD(0)
```

**Result:**
```
FALSE (zero divides exactly by two, so it is even)
```

### 4. A Decimal Value:

```excel
=ISODD(3.7)
```

**Result:**
```
TRUE (3.7 is truncated to 3 before the parity test)
```

### 5. A Negative Number:

```excel
=ISODD(-5)
```

**Result:**
```
TRUE
```

### 6. A Small Negative Decimal:

```excel
=ISODD(-0.9)
```

**Result:**
```
FALSE (truncation toward zero gives 0, which is even)
```

### 7. Banding Alternate Rows:

```excel
=IF(ISODD(ROW()), "Shaded", "Plain")
```

**Result:**
```
Alternates between "Shaded" and "Plain" down the column
```

### 8. Flagging Unpaired Records:

```excel
=IF(ISODD(COUNTA(A1:A100)), "Unpaired record present", "All paired")
```

**Result:**
```
Warns when a list that should hold pairs has an odd number of entries
```

## Notes:

- `ISODD` truncates rather than rounds. `ISODD(2.9)` is `FALSE` because the integer part is `2`, even though `2.9` rounds to `3`.
- `ISODD` is a scalar function. Unlike [`ISTEXT`](./istext.md) or [`ISBLANK`](./isblank.md), it evaluates a single value rather than mapping across a range.
- A value that cannot be converted to a number produces an error rather than `FALSE`. Guard uncertain input with [`ISNUMBER`](../mathematical-functions/is_number.md) first.
- `#N/A` and infinite values are rejected as invalid numeric input.
- `ISODD` is part of the IS family of information functions ([`ISBLANK`](./isblank.md), [`ISERR`](./iserr.md), [`ISERROR`](./iserror.md), [`ISEVEN`](./iseven.md), [`ISLOGICAL`](./islogical.md), [`ISNA`](./isna.md), [`ISNONTEXT`](./isnontext.md), [`ISNUMBER`](../mathematical-functions/is_number.md), `ISODD`, [`ISTEXT`](./istext.md), etc.).

## Applications:

- **Alternating Row Formatting**: Combine with `ROW()` to band a table without a helper column.
- **Batch Assignment**: Split invoices, orders, or users into two balanced groups by identifier parity.
- **Data Validation**: Detect an odd count in a list where every entry should have a matching pair.
- **Scheduling**: Drive fortnightly or every-other-period logic from a week or period number.
- **Checksum Logic**: Implement parity checks in identifier validation routines.

## Related Functions:

- **[ISEVEN](./iseven.md)**: Returns TRUE if the number is even — the exact complement of `ISODD`.
- **[ISNUMBER](../mathematical-functions/is_number.md)**: Returns TRUE if the value is a number; useful as a guard before `ISODD`.
- **[ODD](../mathematical-functions/odd.md)**: Rounds a number up to the nearest odd integer, rather than testing it.
- **[MOD](../mathematical-functions/mod.md)**: Returns the remainder of a division — `MOD(A1,2)=1` is the manual equivalent of `ISODD(A1)`.
- **[TYPE](./type.md)**: Returns a numeric code indicating the data type of a value.
- **[N](./n.md)**: Converts a value to a number — logical `TRUE` becomes `1` and `FALSE` becomes `0`.

> **Tip:** `ISODD` and `ISEVEN` are exact complements, so pick whichever one makes the formula read positively rather than wrapping the other in `NOT`. `IF(ISODD(A1), ...)` is easier to scan six months later than `IF(NOT(ISEVEN(A1)), ...)`.
