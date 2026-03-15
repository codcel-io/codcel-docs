<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# CELL Function

The `CELL` function in Excel is used to **return information about the formatting, location, or contents of a cell**. This is useful for building dynamic formulas that adapt based on cell properties such as address, column, row, data type, or file path.

## Key Features of `CELL`:

- Returns a wide range of metadata about a cell, controlled by an `info_type` text string.
- Can report a cell's address, row number, column number, contents, width, format, protection status, and more.
- When the `reference` argument is omitted, returns information about the last-changed cell.
- Works with cell references and named ranges.
- The `info_type` argument is case-insensitive (e.g., `"row"` and `"ROW"` both work).
- `CELL` is a volatile function — it recalculates whenever the worksheet recalculates, even if its inputs haven't changed.

## Syntax:

```plaintext
CELL(info_type, [reference])
```

- **info_type**: A text string specifying what information to return about the cell. Common values include:
  - `"address"` — Returns the cell address as text (absolute reference).
  - `"col"` — Returns the column number of the cell.
  - `"color"` — Returns `1` if the cell is formatted with a color for negative values; otherwise `0`.
  - `"contents"` — Returns the value in the cell (not the formula).
  - `"filename"` — Returns the full file path, sheet name, and workbook name. Returns empty text if the file has not been saved.
  - `"format"` — Returns a text code corresponding to the number format of the cell.
  - `"parentheses"` — Returns `1` if the cell is formatted with parentheses for positive or all values; otherwise `0`.
  - `"prefix"` — Returns a text value corresponding to the label prefix of the cell (`'` for left-aligned, `"` for right-aligned, `^` for centered, `\` for fill-aligned, empty text for anything else).
  - `"protect"` — Returns `1` if the cell is locked; `0` if not.
  - `"row"` — Returns the row number of the cell.
  - `"type"` — Returns `"b"` for blank, `"l"` for label (text), or `"v"` for value (anything else).
  - `"width"` — Returns the column width of the cell, rounded to the nearest integer.
- **reference** (optional): The cell about which you want information. If omitted, information is returned about the last-changed cell.

## How `CELL` Works:

1. `CELL` takes an `info_type` string that specifies the kind of information to retrieve.
2. If a `reference` is provided, it returns information about that cell. If the reference is a range, it uses the upper-left cell of the range.
3. If `reference` is omitted, `CELL` returns information about the last cell that was changed in the worksheet.
4. Because `CELL` is volatile, it recalculates every time the worksheet recalculates, which can affect performance in large workbooks.

## Examples:

### 1. Cell Address:

```excel
=CELL("address", B5)
```

**Result:**
```
$B$5
```

### 2. Row Number:

```excel
=CELL("row", D10)
```

**Result:**
```
10
```

### 3. Column Number:

```excel
=CELL("col", D10)
```

**Result:**
```
4
```

### 4. Cell Type:

If A1 contains the text `"Hello"`:
```excel
=CELL("type", A1)
```

**Result:**
```
l (indicates a label / text value)
```

### 5. Cell Contents:

If B2 contains `250`:
```excel
=CELL("contents", B2)
```

**Result:**
```
250
```

### 6. Column Width:

```excel
=CELL("width", A1)
```

**Result:**
```
8 (default column width, varies by workbook settings)
```

### 7. Filename and Path:

If the file is saved as `C:\Reports\Sales.xlsx` on Sheet1:
```excel
=CELL("filename", A1)
```

**Result:**
```
C:\Reports\[Sales.xlsx]Sheet1
```

### 8. Conditional Logic Based on Cell Type:

```excel
=IF(CELL("type", A1)="b", "Empty", IF(CELL("type", A1)="l", "Text", "Value"))
```

**Result:**
```
Returns "Empty" if A1 is blank, "Text" if A1 contains text, or "Value" otherwise
```

## Notes:

- When `reference` is a range (e.g., A1:C10), `CELL` uses the upper-left cell of the range (A1 in this case).
- `CELL("filename")` returns an empty string if the workbook has not been saved yet.
- The `"format"` info_type returns codes like `"G"` for General, `"F0"` for fixed with no decimals, `"D1"` for date formats, etc. Refer to Excel documentation for the full list of format codes.
- `CELL` is volatile, meaning it recalculates on every worksheet change. Excessive use in large workbooks may slow performance.
- The `"color"` and `"parentheses"` info_types relate to legacy number formatting and are rarely used in modern Excel.
- `CELL("prefix")` reflects legacy label alignment prefixes and may return empty text in modern versions of Excel for most cells.

## Applications:

- **Dynamic File References**: Use `CELL("filename")` to build formulas that reference the current workbook or sheet name dynamically.
- **Extracting Sheet Names**: Combine `CELL("filename")` with `MID` and `FIND` to extract just the sheet name for use in INDIRECT or other formulas.
- **Input Validation**: Use `CELL("type")` to check whether a cell contains text, a value, or is blank before processing.
- **Conditional Formatting Logic**: Use `CELL("format")` or `CELL("protect")` to drive formula-based conditional formatting or auditing.
- **Debugging**: Inspect cell properties like address, row, column, and width to diagnose formula or layout issues.

## Related Functions:

- **ROW**: Returns the row number of a reference.
- **COLUMN**: Returns the column number of a reference.
- **ADDRESS**: Creates a cell address as a text string from row and column numbers.
- **TYPE**: Returns a numeric code indicating the data type of a value.
- **INFO**: Returns information about the current operating environment.
- **INDIRECT**: Converts a text string into a cell reference.

> **Tip:** `CELL("filename")` is one of the most practical uses of the CELL function — combine it with text functions like `MID`, `FIND`, and `LEN` to dynamically extract the workbook name, path, or sheet name. For example, `=MID(CELL("filename",A1),FIND("]",CELL("filename",A1))+1,255)` extracts the current sheet name.