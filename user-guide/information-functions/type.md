<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# TYPE Function

The `TYPE` function in Excel is used to **return a number that identifies the data type of a value**. This is useful for determining whether a cell contains a number, text, logical value, error, or array, enabling type-aware logic in formulas.

## Key Features of `TYPE`:

- Returns a numeric code representing the data type of a value.
- Distinguishes between numbers, text, logical values, errors, and arrays.
- Works with cell references, constants, and formula results.
- Useful for building dynamic formulas that adapt based on input types.
- Can detect arrays, enabling different handling for single values vs. ranges.

## Syntax:

```plaintext
TYPE(value)
```

- **value**: The value whose data type you want to identify. Can be a number, text, logical value, error value, array, or cell reference.

## How `TYPE` Works:

1. `TYPE` examines the provided value and determines its data type.
2. It returns a numeric code based on the type:
   - **1** — Number
   - **2** — Text
   - **4** — Logical value (TRUE or FALSE)
   - **16** — Error value
   - **64** — Array
3. If the value is a cell reference, `TYPE` evaluates the contents of the referenced cell.
4. If a formula is passed, `TYPE` evaluates the result of the formula and returns the type of that result.

## Examples:

### 1. Number:

```excel
=TYPE(42)
```

**Result:**
```
1
```

### 2. Text:

```excel
=TYPE("Hello")
```

**Result:**
```
2
```

### 3. Logical Value:

```excel
=TYPE(TRUE)
```

**Result:**
```
4
```

### 4. Error Value:

```excel
=TYPE(NA())
```

**Result:**
```
16
```

### 5. Array:

```excel
=TYPE({1,2,3})
```

**Result:**
```
64
```

### 6. Cell Reference Containing a Number:

If A1 contains `100`:
```excel
=TYPE(A1)
```

**Result:**
```
1
```

### 7. Formula Result:

```excel
=TYPE(1/0)
```

**Result:**
```
16 (the division returns a #DIV/0! error, which is an error type)
```

### 8. Conditional Logic Based on Type:

```excel
=IF(TYPE(A1)=2, "Text value", "Not text")
```

**Result:**
```
Returns "Text value" if A1 contains text, otherwise "Not text"
```

## Notes:

- `TYPE` does not distinguish between different kinds of numbers (integers, decimals, dates, times) — all return `1`.
- All error types (`#N/A`, `#VALUE!`, `#REF!`, `#DIV/0!`, `#NAME?`, `#NULL!`, `#NUM!`) return `16`.
- When used on an empty cell, `TYPE` returns `1` (number), since empty cells are treated as zero.
- `TYPE` evaluates the result of a formula, not the formula itself. For example, `TYPE(1+"text")` returns `16` because the formula produces a `#VALUE!` error.
- `TYPE` is particularly useful in LAMBDA functions and helper formulas where inputs may vary in type.

## Applications:

- **Input Validation**: Verify that user inputs are of the expected data type before processing.
- **Dynamic Formulas**: Build formulas that handle different data types gracefully by branching on `TYPE`.
- **Error Detection**: Identify cells containing error values for cleanup or reporting.
- **Array Detection**: Determine whether a value is a single item or an array for conditional processing.
- **Debugging**: Diagnose unexpected formula results by checking the types of intermediate values.

## Related Functions:

- **ISNUMBER**: Returns TRUE if the value is a number.
- **ISTEXT**: Returns TRUE if the value is text.
- **ISLOGICAL**: Returns TRUE if the value is a logical value.
- **ISERROR**: Returns TRUE if the value is any error.
- **ISNA**: Returns TRUE if the value is the #N/A error.
- **N**: Converts values to numbers.

> **Tip:** Use `TYPE` when you need a single formula to handle multiple data types. Instead of nesting `ISNUMBER`, `ISTEXT`, and `ISERROR` checks, a single `TYPE` call can drive a `SWITCH` or nested `IF` to branch on the data type efficiently.