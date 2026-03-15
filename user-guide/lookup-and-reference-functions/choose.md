<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# CHOOSE Function

The `CHOOSE` function in Excel is used to **return a value from a list based on a given index number**. It selects one of the provided values or ranges depending on the specified index. This is useful when you want to dynamically pick a value based on a condition or formula.

## Key Features of `CHOOSE`:

- Returns a value or range corresponding to a specific position.
- Can handle **scalars**, **ranges**, and even **arrays**.
- Supports nesting and can be used inside other functions for conditional logic.

## Syntax:

```plaintext
CHOOSE(index_num, value1, [value2], …)
```

- **index_num**: A number between 1 and 254 that specifies which value to return.
- **value1, value2, …**: A list of up to 254 possible values or references.

## How `CHOOSE` Works:

1. Excel evaluates `index_num`.
2. It selects the nth value from the list of provided arguments.
3. The selected value is returned — it can be a single value, range, or even an array formula.

## Examples:

### 1. Select a Simple Value:

```excel
=CHOOSE(2, "Red", "Green", "Blue")
```

**Result:**
```
Green
```

### 2. Return a Cell Range:

Assume:
- A1:A3 contains `10`, `20`, `30`
- B1:B3 contains `40`, `50`, `60`

```excel
=SUM(CHOOSE(2, A1:A3, B1:B3))
```

**Result:**
```
150
```

Explanation: `CHOOSE` returns `B1:B3`, and `SUM` adds the values: `40 + 50 + 60 = 150`.

### 3. Dynamic Selection:

```excel
=CHOOSE(A1, "Low", "Medium", "High")
```

If `A1` = 3, the result is:
```
High
```

### 4. Use with Arrays:

```excel
=CHOOSE({1,3}, "One", "Two", "Three")
```

**Result:**
```
One   Three
```

This selects multiple items by passing an array of indices.

## Notes:

- If `index_num` is out of bounds (e.g., less than 1 or greater than the number of items), `CHOOSE` returns a `#VALUE!` error.
- All `valueN` arguments are evaluated at the time of function call, even if not selected. This can affect performance or trigger errors.
- Can be nested inside other functions like `IF`, `VLOOKUP`, or `INDEX`.

## Applications:

- **Decision Tables**: Use `CHOOSE` to map numeric codes to labels or actions.
- **Simplified Lookup**: Create small lookup-like structures without needing a separate table.
- **Dynamic Range Selection**: Conditionally select and operate on ranges of cells.

> **Tip:** For more complex conditional logic, consider combining `CHOOSE` with `MATCH` or `IF`.