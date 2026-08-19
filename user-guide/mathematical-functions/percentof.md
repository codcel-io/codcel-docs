<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# PERCENTOF Function

The `PERCENTOF` function in Excel is used to **calculate what fraction of a whole a subset represents**. It sums the subset, sums the whole, and returns the ratio between them. This saves writing `SUM(...)/SUM(...)` by hand and makes share-of-total calculations read more clearly.

`PERCENTOF` is a newer Excel function, available in Microsoft 365.

## Key Features of `PERCENTOF`:

- Returns `SUM(data_subset) / SUM(data_all)` as a **decimal fraction** — `0.2`, not `20%`. Apply a percentage number format to display it as a percentage.
- Accepts scalars or ranges for either argument.
- The two arguments are summed **independently**, so they do not need to be the same size or shape.
- Returns `#DIV/0!` when the whole sums to zero.
- The subset does not have to be contained within the whole; results above `1` (100%) and below `0` are both possible.

## Syntax:

```plaintext
PERCENTOF(data_subset, data_all)
```

- **data_subset**: The value or range making up the part.
- **data_all**: The value or range making up the whole.

## How `PERCENTOF` Works:

1. `PERCENTOF` sums every numeric value in `data_subset`.
2. It sums every numeric value in `data_all`.
3. If the second sum is zero, it returns `#DIV/0!`.
4. Otherwise it returns the first sum divided by the second.

## Examples:

### 1. Two Scalars:

```excel
=PERCENTOF(2, 10)
```

**Result:**
```
0.2 (displays as 20% with a percentage format)
```

### 2. A Range Within a Range:

If A1:A3 contains `1`, `2`, `3`:
```excel
=PERCENTOF(A1:A2, A1:A3)
```

**Result:**
```
0.5 (the first two values sum to 3, the whole column sums to 6)
```

### 3. Share of a Total:

If B2:B5 holds regional sales and B2 is the region of interest:
```excel
=PERCENTOF(B2, B2:B5)
```

**Result:**
```
That region's share of total sales
```

### 4. Division by Zero:

```excel
=PERCENTOF(5, 0)
```

**Result:**
```
#DIV/0!
```

### 5. Ranges of Different Sizes:

If A1:A4 sums to `4` and B1 contains `8`:
```excel
=PERCENTOF(A1:A4, B1)
```

**Result:**
```
0.5 (the arguments are summed independently, so their sizes need not match)
```

### 6. A Subset Larger Than the Whole:

```excel
=PERCENTOF(15, 10)
```

**Result:**
```
1.5 (150% — nothing constrains the subset to be part of the whole)
```

### 7. Negative Values:

```excel
=PERCENTOF(-2, 10)
```

**Result:**
```
-0.2 (negative contributions produce negative shares)
```

### 8. Guarding Against an Empty Total:

```excel
=IFERROR(PERCENTOF(B2, B2:B5), 0)
```

**Result:**
```
Returns 0 instead of #DIV/0! when the total is zero
```

## Notes:

- `PERCENTOF` returns a decimal fraction. Format the cell as a percentage to display `0.2` as `20%`; the underlying value is unchanged.
- `PERCENTOF(x, y)` is equivalent to `SUM(x)/SUM(y)`, including the `#DIV/0!` behaviour when the divisor is zero.
- An empty or all-zero `data_all` produces `#DIV/0!`. A `data_all` whose values cancel out — such as `5` and `-5` — does too.
- An empty `data_subset` sums to zero, so the result is `0`.
- Text and blank cells within either range are ignored by the summation, as they are by `SUM`.
- `PERCENTOF` is a Microsoft 365 function. Older Excel versions will show `#NAME?`; use `SUM(...)/SUM(...)` for backwards compatibility.

## Applications:

- **Share of Total**: Express each region, product, or category as a percentage of the overall figure.
- **Budget Analysis**: Show what proportion of a total budget a line item consumes.
- **Progress Tracking**: Report completed work as a fraction of total planned work.
- **Composition Reporting**: Break a population down into percentage contributions.
- **Variance Analysis**: Compare a subset's contribution across periods without repeating `SUM` twice per formula.

## Related Functions:

- **[SUM](./sum.md)**: Adds all the numbers in a range — the operation `PERCENTOF` applies to each argument.
- **[QUOTIENT](./quotient.md)**: Returns the integer portion of a division.
- **[SUMPRODUCT](./sum_product.md)**: Multiplies corresponding components and returns the sum of those products.
- **[PERCENTILE](../statistical-functions/percentile.md)**: Returns the k-th percentile of values in a range.
- **[IFERROR](../conditional-functions/if_error.md)**: Returns a specified value if a formula evaluates to an error; useful for trapping `#DIV/0!`.

> **Tip:** Because the two arguments are summed independently, `PERCENTOF` will happily compare unrelated ranges. That flexibility is useful — comparing this quarter's subset against last year's total, for example — but it also means a mistyped range produces a plausible-looking number rather than an error. Double-check the second argument really is the whole you meant.
