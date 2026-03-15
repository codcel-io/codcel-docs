<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Error and Warning Codes

When Codcel processes your Excel workbook, it may produce errors or warnings. Each message includes a code (e.g., `T5`, `L12`) that identifies the specific issue.

---

## Code Prefixes

The first part of each code indicates where the issue occurred:

| Prefix | Category | Description |
|--------|----------|-------------|
| **T** | Transpiler | Issues during code generation and transpilation |
| **L** | Loader | Issues loading Excel, CSV, or Parquet files |
| **P** | Parser | Issues parsing cell references and formulas |
| **V** | Validation | Validation issues in the logical model |

### Language-Specific Transpiler Codes

These codes appear when generating code for a specific output target:

| Prefix | Target |
|--------|--------|
| G | Go |
| J | Java |
| PY | Python |
| SW | Swift |
| CLI | Command Line |
| DX | Dioxus Fullstack |
| FFI | FFI Library |
| JNI | JNI Library |
| MCP | MCP Server |
| OA | OpenAPI |
| SRV | Rust Server |
| SCS | C# Server |
| SGO | Go Server |
| SJA | Java Server |
| SKO | Kotlin Server |
| WCC | C# Web Client |
| WCG | Go Web Client |
| WCJ | Java Web Client |
| WCK | Kotlin Web Client |
| WCP | Python Web Client |
| WCR | Rust Web Client |
| WCT | TypeScript Web Client |

---

## Common Transpiler Codes (T)

### T4 - Formula parsing failed

**Type:** Error

**Message:** Error parsing formula at {sheet}!{cell}

**Fix:** Check the formula syntax. Ensure all parentheses are balanced and function names are spelled correctly.

---

### T5 - Unknown Excel function

**Type:** Error

**Message:** Unknown Excel function '{name}' at {sheet}!{cell}

**Fix:** Check that the function name is spelled correctly. See the [Alphabetical Function List](./alphabetical-functions.md) for all supported functions. Some Excel functions are not yet supported by Codcel.

---

### T6 - No calculations to process

**Type:** Error

**Message:** No calculations to process in workbook

**Fix:** Ensure your workbook contains at least one output annotation (`*O*`). Codcel needs annotated outputs to know which cells to transpile. See [Annotations](./annotations.md).

---

### T1 - Combined output must point to an output field

**Type:** Warning

**Message:** The combined output {name} must point to an output field.

**Fix:** Ensure the combined output references a valid cell annotated with `*O*`.

---

## Common Loader Codes (L)

### L12 - Sheet name contains invalid characters

**Type:** Warning

**Message:** Sheet name '{name}' contains characters that are not valid for code generation.

**Fix:** Rename the sheet to use only letters, numbers, and underscores. Avoid spaces and special characters.

---

### L24 - Annotation cell is empty

**Type:** Warning

**Message:** Annotation found at {sheet}!{cell} but the cell below is empty.

**Fix:** Annotations must be placed directly above or to the left of the cell they annotate. Ensure the annotated cell contains a value or formula.

---

### L25 - Invalid annotation syntax

**Type:** Warning

**Message:** Unrecognised annotation '{text}' at {sheet}!{cell}.

**Fix:** Check the annotation syntax. Valid annotations include `*I*`, `*ID*`, `*IX*`, `*O*`, `*T*`, `*U*`, and `*X*`. See [Annotations](./annotations.md).

---

### L26 - Duplicate annotation name

**Type:** Warning

**Message:** Duplicate annotation name '{name}' at {sheet}!{cell}.

**Fix:** Each annotation name must be unique within the workbook. Rename one of the duplicates.

---

### L27 - Table sheet missing T_ prefix

**Type:** Warning

**Message:** Sheet '{name}' appears to contain table data but does not use the T_ prefix.

**Fix:** Table sheets must be named with a `T_` prefix (e.g., `T_Addresses`). Rename the sheet.

---

## Common Parser Codes (P)

### P1 - Invalid cell reference

**Type:** Error

**Message:** Invalid cell reference '{ref}' in formula at {sheet}!{cell}.

**Fix:** Check that the cell reference is valid (e.g., `A1`, `$B$2`, `Sheet1!A1`).

---

### P2 - Circular reference detected

**Type:** Error (when iterative calculation is disabled)

**Message:** Circular reference detected involving cells: {cells}

**Fix:** Either remove the circular reference, or enable iterative calculation in [Settings](./settings.md#enable-iterative-calculation). See [Circular References](./circular-references.md) for guidance.

---

## Common Validation Codes (V)

### V1 - Input type mismatch

**Type:** Warning

**Message:** Input '{name}' has inconsistent types across references.

**Fix:** Ensure the annotated input cell and all cells that reference it use consistent types (number, text, or boolean).

---

## Tips for Troubleshooting

1. **Read the message carefully** -- error messages include the sheet name and cell reference where the issue was found
2. **Check your annotations** -- most loader warnings relate to annotation syntax or placement
3. **Review the function list** -- if you get a T5 error, the function may not be supported yet
4. **Enable iterative calculation** -- if you get circular reference errors and your spreadsheet intentionally uses them
5. **Simplify and test** -- if you get unexpected errors, try creating a minimal spreadsheet that reproduces the issue

---

## See Also

- [Annotations](./annotations.md) -- annotation syntax reference
- [Alphabetical Function List](./alphabetical-functions.md) -- all supported Excel functions
- [Differences from Excel](./differences.md) -- known behavioural differences
- [Settings Reference](./settings.md) -- configuration options