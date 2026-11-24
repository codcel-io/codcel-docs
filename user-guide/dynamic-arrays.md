<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Dynamic Arrays

Dynamic arrays are one of Excel 365's most powerful features. A single formula can return multiple values that "spill" into adjacent cells. Codcel fully supports dynamic array functions and transpiles them into array-returning functions in the generated code.

---

## What Are Dynamic Arrays?

In traditional Excel, a formula in one cell produces one value. With dynamic arrays, a formula can return a range of values. In Excel, these values "spill" into neighbouring cells automatically.

For example, the formula `=SORT(A1:A10)` returns all 10 values sorted, spilling down from the cell containing the formula.

---

## How Codcel Handles Dynamic Arrays

When Codcel transpiles a dynamic array formula, the generated function returns an array (or 2D array) instead of a single value. A result that is one column (for example `FILTER` over one column) is a list; anything else is a list of rows. Every value in the array has the same type, chosen from the formula and the values Excel saved: numbers, text, booleans, dates or times. An array that mixes text and numbers is returned as text.

- **Rust:** `Vec<f64>`, `Vec<String>`, `Vec<Vec<f64>>`, `Vec<Vec<String>>` and so on
- **Java/Kotlin:** `List<Double>`, `List<String>`, `List<List<Double>>` and so on
- **Python:** `list` or `list[list]`
- **C#:** `List<double>`, `List<string>`, `List<List<double>>` and so on
- **JSON (REST API):** JSON arrays

The array has as many values as the formula returns for the inputs given, which need not be the size Excel saved. For example, `=FILTER(G47:G146, B47:B146<>"")` returns one value per non-blank row.

If a dynamic array result is used as an input to another formula, Codcel handles the reference correctly -- just as Excel's spill references work.

---

## Annotating Array Outputs

To mark a dynamic array result as an output, use the standard `*O*` annotation on the cell containing the array formula. The generated code will return the full array.

### Generated tests for array outputs

The generated tests check an array output against everything Excel saved for it: the formula cell and the cells its result spilled into. Each array output is checked in one call. The call first checks the length (or the number of rows and columns), then each value. Numbers are compared within the same tolerance as single values (0.000001); text, booleans, dates and times must be equal. A blank cell in the spill counts as an empty string in a text array and as 0 in a number array.

A very large array is checked on its size and its first 1,000 values, so the test files stay small. Change the limit with `--max-test-array-elements <N>`, or `max_test_array_elements` in the `[cli]` section of the configuration file.

This needs the workbook as Excel saved it. In `.xlsx` and `.xlsb` files Excel records the range each array formula spills into, and Codcel reads the saved values from that range.

To mark an array as an input, use `*I*`, `*ID*`, or `*IX*` annotations. The generated code will accept an array parameter.

---

## Supported Dynamic Array Functions

Codcel supports all standard Excel 365 dynamic array functions:

### Array Generation

| Function | Description |
|----------|-------------|
| [SEQUENCE](./mathematical-functions/sequence.md) | Generate a sequence of numbers |
| [RANDARRAY](./mathematical-functions/rand_array.md) | Generate an array of random numbers |

### Sorting and Filtering

| Function | Description |
|----------|-------------|
| [SORT](./lookup-and-reference-functions/sort.md) | Sort a range |
| [SORTBY](./lookup-and-reference-functions/sortby.md) | Sort a range by another range |
| [FILTER](./table-functions/filter.md) | Filter rows by condition |
| [UNIQUE](./lookup-and-reference-functions/unique.md) | Extract unique values |

### Reshaping

| Function | Description |
|----------|-------------|
| [CHOOSECOLS](./lookup-and-reference-functions/choosecols.md) | Select specific columns |
| [CHOOSEROWS](./lookup-and-reference-functions/chooserows.md) | Select specific rows |
| [DROP](./information-functions/drop.md) | Remove rows or columns from the start/end |
| [TAKE](./information-functions/take.md) | Take rows or columns from the start/end |
| [EXPAND](./lookup-and-reference-functions/expand.md) | Expand an array to specified dimensions |

### Stacking and Wrapping

| Function | Description |
|----------|-------------|
| [HSTACK](./lookup-and-reference-functions/h_stack.md) | Stack arrays horizontally |
| [VSTACK](./lookup-and-reference-functions/v_stack.md) | Stack arrays vertically |
| [TOCOL](./lookup-and-reference-functions/tocol.md) | Convert array to a single column |
| [TOROW](./lookup-and-reference-functions/torow.md) | Convert array to a single row |
| [WRAPCOLS](./lookup-and-reference-functions/wrapcols.md) | Wrap a row into columns |
| [WRAPROWS](./lookup-and-reference-functions/wraprows.md) | Wrap a row into rows |
| [TRANSPOSE](./lookup-and-reference-functions/transpose.md) | Transpose rows and columns |

---

## Limitations

- **Spill references** (`A1#` syntax) are supported when the spill source is a known dynamic array formula
- **Implicit intersection** (`@` operator) behaviour may differ from Excel in edge cases -- see [Differences](./differences.md)
- Dynamic arrays in table columns are not supported -- tables use fixed schemas
- `HSTACK` and `VSTACK` require every input to share the stacking dimension. Excel pads ragged input with `#N/A`; Codcel returns an error instead -- see [HSTACK](./lookup-and-reference-functions/h_stack.md)

---

## See Also

- [Lookup & Reference Functions](./lookup-and-reference-functions.md) -- includes many array-capable functions
- [Annotations](./annotations.md) -- how to annotate inputs and outputs