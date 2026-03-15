<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Dynamic Arrays

Dynamic arrays are one of Excel 365's most powerful features. A single formula can return multiple values that "spill" into adjacent cells. Codcel fully supports dynamic array functions and transpiles them into array-returning functions in the generated code.

---

## What Are Dynamic Arrays?

In traditional Excel, a formula in one cell produces one value. With dynamic arrays, a formula can return a range of values. In Excel, these values "spill" into neighbouring cells automatically.

For example, the formula `=SORT(A1:A10)` returns all 10 values sorted, spilling down from the cell containing the formula.

---

## How Codcel Handles Dynamic Arrays

When Codcel transpiles a dynamic array formula, the generated function returns an array (or 2D array) instead of a single value. The exact representation depends on the output target:

- **Rust:** `Vec<Value>` or `Vec<Vec<Value>>`
- **Java/Kotlin:** `List<Object>` or `List<List<Object>>`
- **Python:** `list` or `list[list]`
- **C#:** `List<object>` or `List<List<object>>`
- **JSON (REST API):** JSON arrays

If a dynamic array result is used as an input to another formula, Codcel handles the reference correctly -- just as Excel's spill references work.

---

## Annotating Array Outputs

To mark a dynamic array result as an output, use the standard `*O*` annotation on the cell containing the array formula. The generated code will return the full array.

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

---

## See Also

- [Lookup & Reference Functions](./lookup-and-reference-functions.md) -- includes many array-capable functions
- [Annotations](./annotations.md) -- how to annotate inputs and outputs