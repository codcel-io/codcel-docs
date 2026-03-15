<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# HSTACK Function

The `HSTACK` function in Excel is used to **horizontally stack values into a single array**. It takes one or more arguments and places each one side-by-side (in columns) to form a new horizontal array. This is particularly useful for combining values from different ranges or constants into a single row-oriented structure.

## Key Features of `HSTACK`:

- Combines values from multiple sources into a single horizontal array.
- Works with both scalar values and arrays.
- Supports dynamic arrays and spills results into adjacent columns.

## Syntax:

```plaintext
HSTACK(array1, [array2], …)
```

- **array1, array2, …**: One or more arrays or values to be stacked horizontally. Scalars are treated as 1×1 arrays.

## How `HSTACK` Works:

1. Each input is evaluated and converted into an array if necessary.
2. Arrays are aligned **row-wise** and concatenated **column-wise**.
3. The final result is a single horizontal array where each input is placed to the right of the previous one.
4. If arrays have differing row counts, Excel pads shorter arrays with blanks.

## Examples:

### 1. Combine Scalar Strings:

```excel
=HSTACK("Apple", "Banana", "Cherry")
```

**Result:**
```
Apple   Banana   Cherry
```

### 2. Combine Ranges Horizontally:

Assume:
- A1:A2 contains `1`, `2`
- B1:B2 contains `3`, `4`

```excel
=HSTACK(A1:A2, B1:B2)
```

**Result:**
```
1   3
2   4
```

### 3. Stack Mixed Scalars and Arrays:

```excel
=HSTACK({"A","B"}, "C", {"D";"E"})
```

**Result:**
```
A   B   C   D
            E
```

Note how `"C"` is broadcasted across two rows to match the height of `{"D";"E"}`.

## Notes:

- `HSTACK` is available in Excel 365 and Excel 2021.
- It automatically resizes the result (spills) to fit the array.
- If used with incompatible types (e.g., arrays with mismatched structures), the function may return a `#SPILL!` error.

## Applications:

- **Dynamic Table Creation**: Combine multiple columns of data into a single structured array.
- **Data Reshaping**: Rearrange vertical or mixed arrays into horizontal format.
- **Report Generation**: Build formatted output ranges by joining different data sources.

> **Tip:** Use `VSTACK` if you want to stack values **vertically** instead of horizontally.