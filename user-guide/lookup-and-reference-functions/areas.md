<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# AREAS Function

The `AREAS` function in Excel is used to **return the number of areas in a reference**. An area is a contiguous range of cells or a single cell. This function is useful for counting how many separate ranges are included in a reference argument, particularly when working with multi-area references.

## Key Features of `AREAS`:

- Returns the count of distinct contiguous ranges within a reference.
- A single cell or a single contiguous range counts as one area.
- Multiple ranges separated by commas (union operator) count as multiple areas.
- Works with named ranges, returning the number of areas the name refers to.
- Useful for validating references and building dynamic formulas that adapt to multi-area inputs.

## Syntax:

```plaintext
AREAS(reference)
```

- **reference**: A reference to a cell, range, or multiple ranges. Multiple areas must be enclosed in an extra set of parentheses when entered directly, e.g., `(A1:B2, C3:D4)`. Can also be a named range.

## How `AREAS` Works:

1. Receives a reference argument that may contain one or more contiguous ranges.
2. Counts the number of distinct contiguous ranges (areas) in the reference.
3. Returns the count as a single number.
4. Each range separated by the union operator (comma) counts as a separate area.
5. A single cell reference counts as one area.

## Examples:

### 1. Single Cell Reference:

```excel
=AREAS(A1)
```

**Result:**
```
1
```

Explanation: A single cell is one contiguous area, so `AREAS` returns 1.

### 2. Single Contiguous Range:

```excel
=AREAS(A1:D5)
```

**Result:**
```
1
```

Explanation: A1:D5 is one contiguous block of cells, so the result is 1.

### 3. Multiple Areas:

```excel
=AREAS((A1:B2, C3:D4, E5:F6))
```

**Result:**
```
3
```

Explanation: The reference contains three separate contiguous ranges, so `AREAS` returns 3. Note the extra parentheses enclosing the multiple ranges.

### 4. Two Areas:

```excel
=AREAS((A1:A10, C1:C10))
```

**Result:**
```
2
```

Explanation: Two separate ranges are provided, so the result is 2.

### 5. Named Range:

If a named range `SalesData` refers to `A1:B10`:

```excel
=AREAS(SalesData)
```

**Result:**
```
1
```

Explanation: The named range refers to a single contiguous range, so `AREAS` returns 1.

### 6. Named Range Referring to Multiple Areas:

If a named range `Regions` is defined as `A1:B5, D1:E5, G1:H5`:

```excel
=AREAS(Regions)
```

**Result:**
```
3
```

Explanation: The named range refers to three separate areas, so `AREAS` returns 3.

### 7. Single Cell Within Multiple Areas:

```excel
=AREAS((A1, B1, C1, D1))
```

**Result:**
```
4
```

Explanation: Each individual cell is its own area, so four single-cell references produce 4.

### 8. Combining with IF for Validation:

```excel
=IF(AREAS(MyRange) > 1, "Multiple areas", "Single area")
```

**Result:**
```
Returns "Multiple areas" or "Single area" depending on whether MyRange contains more than one area
```

Explanation: Uses `AREAS` to check if a named range contains multiple disjoint ranges and responds accordingly.

## Notes:

- The `reference` argument must be enclosed in an extra set of parentheses when specifying multiple ranges directly, e.g., `=AREAS((A1:B2, C3:D4))`. Without the extra parentheses, Excel interprets the comma as a function argument separator rather than a union operator.
- `AREAS` does not count the number of cells — it counts the number of distinct contiguous ranges. Use `ROWS` and `COLUMNS` or `COUNTA` to count cells.
- If the reference is invalid, `AREAS` returns a `#REF!` error.
- Overlapping ranges are still counted as separate areas. For example, `=AREAS((A1:B5, A3:B7))` returns 2, even though the two ranges overlap.
- `AREAS` is particularly useful in conjunction with `INDEX` to extract specific areas from a multi-area reference.

## Applications:

- **Reference Validation**: Verify whether a named range or reference contains the expected number of areas before performing calculations.
- **Dynamic Formula Logic**: Use `AREAS` to build formulas that adapt their behavior based on how many separate ranges are provided.
- **Multi-Area INDEX Extraction**: Combine with `INDEX` to retrieve a specific area from a multi-area reference (e.g., `=INDEX((A1:B2, C3:D4), , , 2)` returns the second area).
- **Data Auditing**: Check named ranges for unexpected multi-area definitions that could cause formula errors.
- **Template Design**: Build flexible templates that adjust calculations based on the number of input areas provided.

## Related Functions:

- **ROWS**: Returns the number of rows in a reference or array.
- **COLUMNS**: Returns the number of columns in a reference or array.
- **INDEX**: Returns a value or reference from a specific position in an array or range — can also select a specific area from a multi-area reference.
- **INDIRECT**: Converts a text string into a cell reference.
- **OFFSET**: Returns a reference to a range offset from a starting cell.
- **COUNTA**: Counts the number of non-empty cells in a range.

> **Tip:** When passing multiple ranges directly to `AREAS`, always use double parentheses: `=AREAS((range1, range2, ...))`. The inner parentheses tell Excel to treat the commas as the union operator rather than as function argument separators.