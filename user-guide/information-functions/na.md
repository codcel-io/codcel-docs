<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# NA Function

The `NA` function in Excel is used to **return the #N/A error value**. This error value indicates that a value is "Not Available" and is commonly used to mark cells where data is missing or not applicable, preventing blank cells from being accidentally included in calculations.

## Key Features of `NA`:

- Returns the `#N/A` error value intentionally.
- Takes no arguments — it's a zero-argument function.
- Prevents blank cells from being misinterpreted as zero in calculations.
- Works with error-handling functions like `ISNA`, `ISBLANK`, and `IFERROR`.
- Useful for flagging missing data in datasets.

## Syntax:

```plaintext
NA()
```

- This function has no parameters. The parentheses are required but empty.

## How `NA` Works:

1. When called, `NA()` immediately returns the `#N/A` error value.
2. The `#N/A` error propagates through calculations — any formula referencing a cell containing `#N/A` will also return `#N/A` (unless error-handled).
3. This behavior is intentional, as it alerts users that required data is missing.
4. Use error-handling functions like `IFERROR` or `IFNA` to manage `#N/A` values in formulas.

## Examples:

### 1. Basic Usage:

```excel
=NA()
```

**Result:**
```
#N/A
```

### 2. Mark Missing Data in a Lookup:

If you want to explicitly show that a lookup value doesn't exist:
```excel
=IF(A1="", NA(), VLOOKUP(A1, B1:C10, 2, FALSE))
```

**Result:**
```
Returns #N/A if A1 is empty, otherwise performs the lookup
```

### 3. Use with ISNA to Check for Missing Values:

```excel
=ISNA(NA())
```

**Result:**
```
TRUE
```

### 4. Use with IFNA to Handle Missing Values:

```excel
=IFNA(VLOOKUP("Unknown", A1:B10, 2, FALSE), "Not Found")
```

**Result:**
```
"Not Found" (if the lookup returns #N/A)
```

### 5. Fill Empty Cells with NA:

```excel
=IF(A1="", NA(), A1)
```

**Result:**
```
Returns #N/A if A1 is empty, otherwise returns the value in A1
```

### 6. Exclude Missing Data from Charts:

When charting data with missing values:
```excel
=IF(B1="", NA(), B1)
```

**Result:**
```
Charts will show a gap where #N/A appears (in line charts)
```

### 7. Use in Array Formulas:

```excel
=IF(A1:A5="", NA(), A1:A5)
```

**Result:**
```
Returns #N/A for empty cells, preserving actual values otherwise
```

### 8. Combine with IFERROR for Default Values:

```excel
=IFERROR(100/A1, NA())
```

**Result:**
```
Returns #N/A instead of #DIV/0! if A1 is zero
```

## Notes:

- `NA()` is different from typing `#N/A` directly — the function generates a true error value.
- The `#N/A` error is distinct from other errors like `#VALUE!`, `#REF!`, or `#DIV/0!`.
- Use `ISNA()` to test specifically for `#N/A` errors, or `ISERROR()` to test for any error.
- In line charts, `#N/A` values create gaps, while zero values create points on the axis.
- `NA()` is useful for data integrity — it makes missing data explicit rather than hidden.

## Applications:

- **Data Validation**: Mark cells where required data hasn't been entered.
- **Lookup Fallbacks**: Indicate when lookup values don't exist in reference tables.
- **Chart Gaps**: Create intentional gaps in line charts for missing data points.
- **Error Propagation**: Ensure calculations fail visibly when dependent data is missing.
- **Data Quality**: Distinguish between "zero" and "not available" in datasets.

## Related Functions:

- **ISNA**: Tests whether a value is the `#N/A` error.
- **IFNA**: Returns a specified value if a formula returns `#N/A`, otherwise returns the formula result.
- **IFERROR**: Returns a specified value if a formula returns any error.
- **ISERROR**: Tests whether a value is any error.
- **N**: Converts values to numbers (returns 0 for text and errors).

> **Tip:** Use `NA()` instead of leaving cells blank when data is genuinely missing. This makes your spreadsheets more reliable by ensuring that missing data is handled explicitly rather than being silently treated as zero in calculations.