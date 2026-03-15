<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# N Function

The `N` function in Excel is used to **convert values to numbers**. It returns the numeric value of its argument if the argument is a number, date, or logical value, and returns 0 for text values. This function is primarily used for compatibility with other spreadsheet programs and for ensuring numeric calculations work correctly.

## Key Features of `N`:

- Converts various data types to their numeric equivalents.
- Returns **0** for text values and empty cells.
- Handles **dates**, **times**, **logical values**, and **error values**.
- Useful for data validation and ensuring numeric operations.

## Syntax:

```plaintext
N(value)
```

- **value**: The value you want to convert to a number. Can be a number, text, logical value, date, time, or cell reference.

## How `N` Works:

1. If the value is already a number, `N` returns that number unchanged.
2. If the value is a date or time, `N` returns the serial number representation.
3. If the value is `TRUE`, `N` returns 1; if `FALSE`, returns 0.
4. If the value is text or an empty cell, `N` returns 0.
5. If the value is an error, `N` returns the error.

## Examples:

### 1. Convert Numbers:

```excel
=N(42)
```

**Result:**
```
42
```

### 2. Convert Text:

```excel
=N("Hello")
```

**Result:**
```
0
```

### 3. Convert Logical Values:

```excel
=N(TRUE)
=N(FALSE)
```

**Results:**
```
1
0
```

### 4. Convert Dates:

```excel
=N("1/1/2024")
```

**Result:**
```
45292
```

(The serial number for January 1, 2024)

### 5. Handle Mixed Data:

If cell A1 contains "123" (as text):
```excel
=N(A1)
```

**Result:**
```
0
```

If cell A1 contains 123 (as number):
```excel
=N(A1)
```

**Result:**
```
123
```

### 6. Array Usage:

```excel
=N({TRUE, "Text", 42, FALSE})
```

**Result:**
```
1   0   42   0
```

## Notes:

- `N` does not convert text that looks like numbers (e.g., "123" remains 0, not 123).
- For actual text-to-number conversion, use `VALUE` function instead.
- Empty cells return 0 when processed by `N`.
- Error values are passed through unchanged.

## Applications:

- **Data Cleaning**: Identify non-numeric values in datasets.
- **Compatibility**: Ensure formulas work across different spreadsheet programs.
- **Conditional Logic**: Use with other functions to handle mixed data types.
- **Array Formulas**: Convert arrays of mixed data to numeric equivalents.

## Related Functions:

- **VALUE**: Converts text that represents numbers to actual numbers.
- **ISNUMBER**: Tests whether a value is a number.
- **TYPE**: Returns the data type of a value.

> **Tip:** While `N` is available in Excel, it's rarely used in modern Excel formulas. Consider `VALUE` for text-to-number conversion or `ISNUMBER` for data type checking instead.