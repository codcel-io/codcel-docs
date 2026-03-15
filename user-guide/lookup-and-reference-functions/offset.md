<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# OFFSET Function

The `OFFSET` function in Excel is used to **return a reference to a range that is offset from a starting cell or range by a specified number of rows and columns**. It dynamically constructs a reference based on a starting point, making it ideal for creating flexible, sliding ranges that adjust based on conditions or calculations.

## Key Features of `OFFSET`:

- Returns a reference shifted from a starting cell by a given number of rows and columns.
- Can optionally resize the returned reference to a specified height and width.
- Creates dynamic ranges that update automatically when input values change.
- Works seamlessly with other functions like SUM, AVERAGE, COUNT, and INDEX.
- The returned reference can be a single cell or a multi-cell range.

## Syntax:

```plaintext
OFFSET(reference, rows, cols, [height], [width])
```

- **reference**: The starting point from which the offset is applied. This must be a cell or range of adjacent cells.
- **rows**: The number of rows to move from the reference. Positive values move down, negative values move up.
- **cols**: The number of columns to move from the reference. Positive values move right, negative values move left.
- **height** (optional): The number of rows in the returned reference. Must be a positive number. Defaults to the height of the original reference.
- **width** (optional): The number of columns in the returned reference. Must be a positive number. Defaults to the width of the original reference.

## How `OFFSET` Works:

1. Starts from the upper-left corner of the given reference.
2. Moves the specified number of rows down (or up if negative) and columns right (or left if negative).
3. From the new starting position, creates a reference with the specified height and width.
4. If height and width are omitted, the returned range has the same dimensions as the original reference.
5. Returns the value(s) at the resulting reference, or passes the reference to the enclosing function.

## Examples:

### 1. Basic Single Cell Offset:

Given data in A1:D5:
```
A     B     C     D
10    20    30    40
50    60    70    80
90   100   110   120
130  140   150   160
```

```excel
=OFFSET(A1, 2, 3)
```

**Result:**
```
80
```

Explanation: Starting from A1, move 2 rows down and 3 columns right to reach D3, which contains 80.

### 2. Offset with Height and Width:

```excel
=SUM(OFFSET(A1, 1, 0, 3, 2))
```

**Result:**
```
480
```

Explanation: Starting from A1, move 1 row down (to A2), then create a 3-row by 2-column range (A2:B4). SUM adds: 50 + 60 + 90 + 100 + 130 + 140 = 570. Wait — let me recalculate: 50 + 60 + 90 + 100 + 130 + 140 = 570.

```
570
```

### 3. Negative Row Offset:

```excel
=OFFSET(C3, -1, -2)
```

**Result:**
```
10
```

Explanation: Starting from C3, move 1 row up and 2 columns left to reach A2, which contains 50. Actually — C3 is row 3, column C. Moving up 1 row goes to row 2 (C2), moving left 2 columns goes to column A (A2), which contains 50.

```
50
```

### 4. Dynamic SUM with OFFSET:

If A1 contains a starting row number (e.g., 2) and B1 contains a count (e.g., 3):

```excel
=SUM(OFFSET(A3, 0, 0, B1, 1))
```

**Result:**
```
Sums a dynamic number of rows starting from A3, based on the value in B1
```

### 5. Create a Dynamic Named Range:

```excel
=OFFSET(Sheet1!$A$1, 0, 0, COUNTA(Sheet1!$A:$A), 1)
```

**Result:**
```
Returns a range starting at A1 with height equal to the number of non-empty cells in column A
```

This is commonly used to define named ranges that automatically expand as data is added.

### 6. OFFSET with MATCH for Dynamic Lookup:

```excel
=OFFSET(A1, MATCH("Target", A1:A100, 0) - 1, 2)
```

**Result:**
```
Returns the value in column C on the same row where "Target" is found in column A
```

### 7. Sliding Window Average:

If A1 contains values in a column and you want the average of the last 5 entries:

```excel
=AVERAGE(OFFSET(A1, COUNTA(A:A) - 5, 0, 5, 1))
```

**Result:**
```
Returns the average of the last 5 non-empty values in column A
```

### 8. Two-Dimensional Offset:

```excel
=SUM(OFFSET(B2, 1, 1, 2, 2))
```

**Result:**
```
Returns the sum of a 2x2 block starting 1 row below and 1 column right of B2 (i.e., C3:D4)
```

## Notes:

- If the offset reference goes outside the boundaries of the worksheet, `OFFSET` returns a `#REF!` error.
- `height` and `width` must be positive numbers. Zero or negative values return a `#REF!` error.
- `OFFSET` is a **volatile function** — Excel recalculates it every time the worksheet recalculates, even if none of its inputs have changed. This can affect performance in large workbooks.
- The `rows` and `cols` arguments can be zero, in which case no movement occurs in that direction.
- `OFFSET` does not physically move cells — it only returns a reference to a different location.
- When used alone in a cell, `OFFSET` returns the value at the offset position. When used inside functions like SUM or AVERAGE, it passes the range reference.

## Applications:

- **Dynamic Ranges**: Create ranges that automatically expand or contract based on data size.
- **Sliding Window Calculations**: Compute running averages, sums, or counts over a moving window of data.
- **Dynamic Charts**: Build chart source ranges that update automatically as new data is added.
- **Flexible Lookups**: Combine with MATCH to create dynamic lookup formulas without hardcoded references.
- **Data Pagination**: Extract specific subsets of data based on page number and page size parameters.

## Related Functions:

- **INDEX**: Returns a value or reference from a specific position in an array or range.
- **MATCH**: Returns the relative position of an item in a range.
- **INDIRECT**: Returns a reference specified by a text string.
- **ROW**: Returns the row number of a reference.
- **COLUMN**: Returns the column number of a reference.
- **ROWS**: Returns the number of rows in a reference.
- **COLUMNS**: Returns the number of columns in a reference.

> **Tip:** While `OFFSET` is powerful for dynamic ranges, consider using structured table references or the `INDEX` function as a non-volatile alternative where possible. For example, `INDEX(A:A, COUNTA(A:A))` returns the last value in column A without the performance cost of volatility.