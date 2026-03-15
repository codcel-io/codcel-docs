<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Named Ranges

Excel's Name Manager allows you to assign names to cells or ranges of cells. Codcel reads these defined names from your workbook and uses them during transpilation.

---

## How Codcel Handles Named Ranges

When you import an Excel workbook, Codcel extracts all defined names and resolves them to their cell references. If a formula uses a named range, Codcel replaces it with the actual cell reference during transpilation.

For example, if you define a name `TaxRate` pointing to cell `B2`, a formula like `=Price * TaxRate` is resolved to `=Price * B2` before code generation.

---

## Supported Named Range Types

| Type | Supported | Notes |
|------|-----------|-------|
| Single cell reference | Yes | e.g., `TaxRate` → `Sheet1!$B$2` |
| Cell range reference | Yes | e.g., `Prices` → `Sheet1!$A$1:$A$100` |
| Cross-sheet references | Yes | e.g., `Config.Rate` → `Config!$B$2` |
| Named constants | Yes | e.g., `Pi` → `3.14159` |
| Named LAMBDAs | Yes | Including recursive LAMBDAs. See [LAMBDA Support](./differences/lambda-support.md) |

---

## Best Practices

- **Use descriptive names** -- named ranges make your Excel workbook more readable and Codcel's generated code more maintainable
- **Avoid special characters** -- stick to letters, numbers, and underscores in names for cleanest code generation
- **Keep scope simple** -- workbook-scoped names are preferred over sheet-scoped names

---

## See Also

- [LAMBDA Support](./differences/lambda-support.md) -- named LAMBDA support details
- [Excel Guidelines](./codcel-excel-guidelines.md) -- preparing your workbook for Codcel