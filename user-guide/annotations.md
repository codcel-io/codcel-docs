<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Annotations

Annotations are special markers you place in Excel cells to tell Codcel which cells are **inputs**, **outputs**, and **tables**. They are the primary way you communicate the structure of your spreadsheet to the code generator.

- All annotations are enclosed in asterisks (`*`)
- Annotations must be placed in **text/string cells** (not in number or formula cells)
- Names in annotations are automatically converted to **snake_case** in the generated code
- Annotations can be placed in **any cell on any sheet**

---

## Quick Reference

| Annotation | Format | Purpose |
|------------|--------|---------|
| `*I*` | `*I*CellRef*Name` | Required input parameter |
| `*ID*` | `*ID*CellRef*Name` | Input with default value (optional) |
| `*IX*` | `*IX*CellRef*Name` | Optional input with no default |
| `*O*` | `*O*CellRef*Name` | Calculation output |
| `*T*` | `*T*Range*CRUDOps*TableName` | CRUD table definition |
| `*U*` | `*U*ColumnName` (in table header) | Unique column constraint |
| `*X*` | `*X*ColumnName` (in table header) | Optional column |

---

## Input Annotations

Input annotations mark cells whose values should be provided by the caller when running the generated code. There are three types, each with different behaviour for how the input is treated.

### `*I*` -- Required Input

**Format:** `*I*CellRef*Name`

Marks a cell as a **required** input parameter. The caller must always provide a value for this input.

**Example:**

|       | A                        | B     |
|-------|--------------------------|-------|
| **1** | `*I*B1*InterestRate`     | 0.05  |
| **2** | `*I*B2*LoanAmount`       | 250000 |

- `*I*` declares this as a required input
- `B1` is the cell that holds the input value
- `InterestRate` is the name of the input (becomes `interest_rate` in generated code)

When the generated code runs, the caller must supply values for `interest_rate` and `loan_amount`. The values in cells B1 and B2 (0.05 and 250000) are used during code generation to verify that calculations produce the expected results.

---

### `*ID*` -- Input with Default Value

**Format:** `*ID*CellRef*Name`

Marks a cell as an **optional** input parameter **with a default value**. If the caller does not provide a value, the value currently in the referenced cell is used as the default.

**Example:**

|       | A                         | B    |
|-------|---------------------------|------|
| **1** | `*ID*B1*DiscountRate`     | 0.10 |

- If the caller provides a value for `discount_rate`, that value is used
- If the caller omits `discount_rate`, the default value `0.10` from cell B1 is used

Use `*ID*` when your input has a sensible default that most callers will not need to change.

---

### `*IX*` -- Optional/Extra Input

**Format:** `*IX*CellRef*Name`

Marks a cell as a **fully optional** input parameter with **no default value**. The caller can omit this input entirely.

**Example:**

|       | A                    | B             |
|-------|----------------------|---------------|
| **1** | `*IX*B1*Notes`       | Sample note   |

- If the caller provides a value for `notes`, it is used
- If the caller omits `notes`, no value is set

Use `*IX*` for inputs that extend functionality but are not needed for the core calculation.

---

### Input Type Comparison

| Annotation | Required? | Has Default? | Behaviour When Omitted |
|------------|-----------|--------------|------------------------|
| `*I*` | Yes | No | Caller must provide a value |
| `*ID*` | No | Yes (from cell value) | Uses the cell's value as default |
| `*IX*` | No | No | Input is simply absent |

---

## Output Annotations

Output annotations mark cells whose calculated values should be returned by the generated code.

### `*O*` -- Output

**Format:** `*O*CellRef*Name`

Marks a cell as a **calculation output**. The generated code exposes this value as a return value, API endpoint, or function result.

**Example:**

|       | A                          | B                          |
|-------|----------------------------|----------------------------|
| **1** | `*O*B1*MonthlyPayment`     | =PMT(0.05/12, 30\*12, -250000) |

- `*O*` declares this as an output
- `B1` is the cell containing the formula or value to output
- `MonthlyPayment` is the output name (becomes `monthly_payment` in generated code)

> **Important:** Every Codcel project must have **at least one** `*O*` annotation.

---

### Combined Outputs

You can create a single output that returns multiple values by listing cell references separated by semicolons.

**Format:** `*O*CellRef1;CellRef2;CellRef3*Name`

**Example:**

|       | A                                  | B      | C      | D      |
|-------|------------------------------------|--------|--------|--------|
| **1** | `*O*B1;C1;D1*LoanSummary`         | 1342   | 483120 | 233120 |

This creates a single output called `loan_summary` that returns the values from cells B1, C1, and D1 together.

Use combined outputs when you want a single function or endpoint to return a group of related values.

---

## Table Annotations

Table annotations define database-backed CRUD tables. For a complete guide including PostgreSQL setup, API endpoints, and data management, see [CRUD Tables](./crud-tables.md).

### `*T*` -- CRUD Table

**Format:** `*T*Range*CRUDOps*TableName` or `*T*Range*CRUDOps*I*TableName`

Defines a table with Create, Read, Update, and/or Delete operations.

**Example:**

```
*T*Persons!A1:Persons!E4*CRUD*I*Persons
```

| Part | Meaning |
|------|---------|
| `*T*` | Declares this as a table annotation |
| `Persons!A1:Persons!E4` | The range of the table (first row = headers) |
| `*CRUD*` | Which operations to enable: **C**reate, **R**ead, **U**pdate, **D**elete |
| `*I*` | *(Optional)* Insert the Excel rows into the database on creation |
| `Persons` | The database table name |

You can enable any combination of operations. For example, `*CR*` enables only Create and Read, while `*RU*` enables only Read and Update.

---

### Column Modifiers

Column modifiers are placed at the start of a header cell in a CRUD table to add constraints to individual columns.

#### `*U*` -- Unique Column

Marks a column as having a **uniqueness constraint**. No two rows can have the same value in this column.

**Example header cell:** `*U*Email`

#### `*X*` -- Optional Column

Marks a column as **optional**. Rows can be created without providing a value for this column.

**Example header cell:** `*X*Date of Birth`

> **Note:** Even when a column is optional, the first data row must contain a value so that Codcel can infer the data type.

**Example table with column modifiers:**

|   | A        | B           | C              | D                  | E         |
|---|----------|-------------|----------------|--------------------|-----------|
| 1 | **Name** | **Surname** | **\*U\*Email** | **\*X\*Date of Birth** | **Phone** |
| 2 | John     | Smith       | john.s@example.com | 1985-03-15 | 555-0123  |

For full details on CRUD table setup, searching, and PostgreSQL integration, see [CRUD Tables](./crud-tables.md).

---

## Placement Rules

### Where to Place Annotations

Annotation cells can be placed **anywhere** in your workbook -- they do not need to be adjacent to the cells they reference. A common pattern is to dedicate a sheet (e.g. "Codcel" or "Config") for all your annotations, keeping your calculation sheets clean.

### Cell Reference Formats

| Reference Type | Format | Example |
|---------------|--------|---------|
| Same-sheet cell | `CellAddress` | `B2` |
| Cross-sheet cell | `SheetName!CellAddress` | `Sheet2!B2` |
| Table range | `SheetName!Start:SheetName!End` | `Persons!A1:Persons!E4` |

### Cross-Sheet References

Annotations on one sheet can reference cells on a different sheet:

|       | A                            | B |
|-------|------------------------------|---|
| **1** | `*I*Calculations!B5*TaxRate` |   |
| **2** | `*O*Calculations!D10*Total`  |   |

```
---- SHEET: Codcel ----
```

This places the annotations on the "Codcel" sheet while the actual input and output cells live on the "Calculations" sheet.

---

## Complete Example

Here is a complete mortgage calculator example showing how annotations, inputs, outputs, and formulas work together.

### Calculation Sheet

|       | A                 | B                              |
|-------|-------------------|--------------------------------|
| **1** | Interest Rate     | 0.05                           |
| **2** | Loan Amount       | 250000                         |
| **3** | Term (Years)      | 30                             |
| **4** | Monthly Payment   | =PMT(B1/12, B3\*12, -B2)      |
| **5** | Total Cost        | =B4\*B3\*12                    |

```
---- SHEET: Calc ----
```

### Annotation Sheet

|       | A                             |
|-------|-------------------------------|
| **1** | `*I*Calc!B1*InterestRate`     |
| **2** | `*I*Calc!B2*LoanAmount`       |
| **3** | `*ID*Calc!B3*TermYears`       |
| **4** | `*O*Calc!B4*MonthlyPayment`   |
| **5** | `*O*Calc!B5*TotalCost`        |

```
---- SHEET: Codcel ----
```

### What Gets Generated

From these annotations, Codcel generates:

- **Two required inputs**: `interest_rate` (f64) and `loan_amount` (f64)
- **One optional input with default**: `term_years` (f64, default: 30)
- **Two outputs**: `monthly_payment` (f64) and `total_cost` (f64)
- **A calculation function** that takes the inputs and returns the outputs
- **REST API endpoints** (if the server target is enabled) for calling the calculation
- **Test cases** that verify the generated code matches the Excel results

---

## Common Warnings

If your annotations have issues, Codcel displays warnings during import. Here are the most common:

| Code | Meaning | Solution |
|------|---------|----------|
| L24 | Unrecognised annotation pattern (e.g. `*Z*`) | Check for typos. Valid annotations: `*I*`, `*ID*`, `*IX*`, `*O*`, `*T*`. Valid column modifiers: `*U*`, `*X*`. |
| L25 | Empty name in annotation | Provide a name between the asterisks, e.g. `*I*B1*MyInput` |
| L26 | Invalid CRUD operation character | Use only the letters C, R, U, and D |
| L27 | Annotation found in a non-string cell | Move the annotation to a text cell -- annotations must be in string cells |

---

## Next Steps

- [Excel to Code](./excel-to-code.md) -- the complete workflow from spreadsheet to generated project
- [CRUD Tables](./crud-tables.md) -- full guide to database-backed tables with CRUD operations
- [UI Configuration](./ui-configuration.md) -- configure generated user interfaces from within Excel
- [Settings Reference](./settings.md) -- all project configuration options