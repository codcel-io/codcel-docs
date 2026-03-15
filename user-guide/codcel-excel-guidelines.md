<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Preparing Excel Files for Use with Codcel

To ensure smooth code generation, follow these guidelines when preparing your `.xlsx` files.

---

## What Should Be in the File

- Named sheets (no duplicates)
- Standard Excel formatting
- UTF-8 compatible characters

---

## What Should NOT Be in the File

Codcel does **not** support or may hang/crash on:

| Feature                         | Problem                              |
|----------------------------------|---------------------------------------|
| Chartsheets                     | Unsupported format                    |
| Embedded objects (e.g. images)  | May lead to unexpected behavior       |
| External links                  | Can create infinite lookups           |
| Hidden sheets with formulas     | Sometimes parsed, sometimes skipped   |
| Printer settings (`.bin`)       | Unnecessary and can confuse parser    |
| Comments and VML drawings       | Not parsed, may slow down reading     |
| Custom XML mappings             | Ignored and can bulk up file size     |
| Large `calcChain.xml` files     | Can create infinite loops or hangs    |

---

## How to Clean Your Excel File

### 1. Remove External Links
Go to:
```
Data > Queries & Connections > Edit Links > Break Links
```

### 2. Save a Clean Copy
In Excel:
```
File > Save As > .xlsx (choose a new filename)
```
This rewrites the internal structure and strips unused junk.

### 3. Remove Comments and Drawings
- In Excel: `Review > Delete All Comments`
- Manually: unzip `.xlsx` and delete `xl/comments*.xml` and `xl/drawings/`

### 4. Remove Hidden Sheets
- Right-click sheet tabs > Unhide > Delete unnecessary sheets

### 5. Optional: Use LibreOffice
LibreOffice tends to save cleaner `.xlsx` files with less legacy clutter.

---

**By following these steps, you can ensure your Excel files work seamlessly with Codcel.**

**Next:** Learn how to annotate your inputs, outputs, and tables in the [Annotations](./annotations.md) guide.