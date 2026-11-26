<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# VBA Functions

A formula can call a function written in the workbook's VBA, for example `=PremiumRate(B2, B3)`. Codcel converts formulas, not VBA, so it handles such a call like this:

1. Codcel reads the VBA project in the workbook (`.xlsm`, `.xlsb`, `.xls`) and finds the function the formula calls.
2. The generated code calls a Rust function in its place, one Rust function per VBA function.
3. You write that Rust function once. Codcel gives you a stub to start from, which holds the original VBA, and tests built from the results Excel saved.

Every target language uses the same Rust, because the other languages call the Rust calculation library.

## The generated files

In the Rust calculation library (`<project>-calculation/src`):

| File | Owner | What it holds |
|---|---|---|
| `vba_manual.rs` | **You** | One function per VBA function, to write in Rust. Codcel writes this file once and **never overwrites it**, even with `--clean`. |
| `vba/mod.rs` | Codcel | Lists each VBA function, its Rust function and the cells that call it. Replaced on every generation. |
| `vba/tests.rs` | Codcel | A test for each cell whose formula is just the call. It checks the Rust against the value Excel saved. Replaced on every generation. |

Each stub in `vba_manual.rs` looks like this:

```rust
/// `Pricing.PremiumRate`, the VBA function the formulas call as `PremiumRate`.
///
/// Called from Quote!B7, Quote!B8.
///
/// VBA returns: `Double`
///
/// VBA arguments:
/// - `age`: `ByVal Age As Integer`
/// - `term`: `ByVal Term As Integer`
//
// TODO(codcel-vba): convert Pricing.PremiumRate to Rust.
//
// Original VBA (Pricing, lines 8-15):
//    8 | Public Function PremiumRate(ByVal Age As Integer, ByVal Term As Integer) As Double
//    9 |     If Age < 18 Or Term <= 0 Then
//  ...
pub fn premium_rate(age: Value, term: Value) -> Result<Value, Box<dyn Error + Send + Sync>> {
    let _ = (&age, &term);
    Err(crate::vba::not_converted("Pricing.PremiumRate"))
}
```

The stub also lists the other VBA procedures the function calls, with their source, and a few of the results Excel saved.

To find every function still to write, search for `TODO(codcel-vba)`.

## Writing a function

Replace the stub's body with Rust that does what the VBA does.

- **Arguments.** Each argument is a `Value`:
    - a number is `Value::F64`;
    - text is `Value::String`;
    - TRUE or FALSE is `Value::Bool`;
    - a blank cell, or an optional argument the formula left out, is `Value::None`;
    - a range is `Value::AreaValue`, a `Vec` of rows, each a `Vec` of cells.
- **`ParamArray`.** A `ParamArray` parameter arrives as one `Vec<Value>`.
- **Return value.** Return the value the cell should show, for example `Ok(Value::F64(rate))`.
- **Errors.** For an error the VBA would give, return `Ok(Value::Error(ExcelError::Value))`, which shows as `#VALUE!`.
- **Unwritten functions.** Until a function is written, the cells that call it return an error that names the function. No wrong value is calculated.

Check your work with:

```bash
cd <project>-calculation
cargo test vba
```

## When the VBA changes

Generate again as usual. Your `vba_manual.rs` is kept.

If the formulas now call a VBA function your file does not have yet, Codcel writes its stub to `vba_manual.rs.new` and says so. Copy the stub into `vba_manual.rs`. Once every function is there, Codcel removes the `.new` file on the next generation.

## What Codcel reports

| Code | When |
|---|---|
| [T31](./error-codes.md#t31-a-formula-calls-a-vba-function) | A formula calls a VBA function. Its Rust is in `vba_manual.rs`. |
| [T32](./error-codes.md#t32-vba-procedure-cannot-be-called-from-a-cell) | A formula calls a VBA procedure that a cell cannot call, or a name two modules define. |
| [T33](./error-codes.md#t33-vba-that-codcel-does-not-run) | The workbook has macros or event procedures, which Codcel does not run. |
| [L36](./error-codes.md#l36-vba-project-could-not-be-read) | The workbook's VBA project could not be read. |

## What a cell can call

Excel lets a cell call only some VBA procedures, and Codcel follows the same rules:

- **Allowed:** a `Public` (or undeclared) `Function` in a standard module.
- **Not allowed:**
    - `Sub`s;
    - `Private` functions;
    - functions in sheet, `ThisWorkbook`, class or form modules;
    - functions in a module with `Option Private Module`.
- **Same name in two modules:** write the module in the formula, for example `=Pricing.Rate(A1)`.

Conditional compilation (`#If ... Then`) is read as 64-bit Excel on Windows.

## VBA that does not compute a cell

Some VBA changes the workbook instead of computing a cell:

- event procedures such as `Workbook_Open` and `Worksheet_Change`;
- macros run from a button.

The generated code does not run this VBA. It works from the values the workbook was saved with, and Codcel lists such procedures in warning T33.

If a macro changes cells that an output depends on, do one of these:

- move that logic into formulas;
- make those cells inputs.
