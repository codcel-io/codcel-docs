<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Inputs & Outputs

Codcel has always let you declare inputs and outputs by placing `*I*` and `*O*` annotations in
your spreadsheet. **That workflow is unchanged.**

What this page describes is the **review step** built on top of it: a single list of everything
the generated code will expose, where each entry can be selected or deselected, renamed, and --
for inputs -- set to Required, Default or Extra, all **without editing the spreadsheet**. Codcel
can also **auto-detect** likely inputs and outputs from cells you have not marked, and add them
to the same list as suggestions for you to accept or reject.

The review step is available in both the [desktop application](./desktop-app.md) and the
[command line interface](./cli.md), and your choices are stored in a small, human-editable
`codcel-io.toml` file that both tools read and write.

---

## How It Relates to Annotations

The list always starts from the annotations already in your workbook:

| Annotation | Meaning |
|------------|---------|
| `*I*A1*Name` | Required input at `A1`, named `Name` |
| `*ID*A1*Name` | Input with a default value (optional) |
| `*IX*A1*Name` | Optional/extra input with no default |
| `*O*A1*Name` | Output at `A1`, named `Name` |

See [Annotations](./annotations.md) for the full annotation reference.

Two rules govern how the review step and your annotations interact:

- **Annotations come first, detection is on request.** The list opens showing only the inputs
  and outputs your workbook already declares. Auto-detection is a separate, explicit action --
  the **Auto-detect** button in the desktop app, or the `--detect-io` / `--detect-io-interactive`
  flags on the CLI.
- **Detection supplements annotations, it never replaces them.** Auto-detection only considers
  cells that are *not* already annotated, so you can hand-mark the tricky cells and auto-detect
  the rest in the same workbook. A suggestion can never take over an annotated cell.

---

## What Gets Detected

Auto-detection deliberately errs on the side of quiet:

- **Outputs** are *terminal* formula cells -- formulas whose result is not consumed by another
  formula. Intermediate formulas are excluded.
- **Inputs** are literal (non-formula) cells that are *referenced* by at least one formula.
  Stray literals that nothing depends on are excluded.

Each detected candidate is given a suggested **label** taken from an adjacent cell: the text
immediately to its left, otherwise the text directly above it, falling back to the cell
reference itself. You can rename any label before generating.

---

## The `codcel-io.toml` File

Your selections are saved to a `codcel-io.toml` sidecar file. It is plain TOML and safe to edit
by hand or to keep in version control.

```toml
# The workbook's own *O*B4*Total annotation, renamed
[[io]]
kind = "Output"
sheet = "Sheet1"
cell = "B4"
selected = true
label = "Grand Total"
from_marker = true

# An auto-detected suggestion that was accepted
[[io]]
kind = "Input"
sheet = "Sheet1"
cell = "B6"
selected = true
label = "Price 2"
field_option = "Required"
from_marker = false
```

| Field | Description |
|-------|-------------|
| `kind` | `"Input"` or `"Output"` |
| `sheet` | Name of the worksheet containing the cell |
| `cell` | Cell reference (for a range input, the range's start cell) |
| `selected` | `false` drops the entry from the generated code |
| `label` | The name used for the generated field (converted to snake_case in code) |
| `field_option` | Inputs only: `"Required"`, `"Default"` or `"Extra"` |
| `from_marker` | `true` if the row describes a cell that is already annotated in the workbook |

Notes on behaviour:

- Setting `selected = false` on a `from_marker = true` row **suppresses the annotation itself**:
  the cell keeps its value in the calculation but stops being an input or output field.
- Setting `field_option` on a `from_marker = true` row is how you turn an `*I*` into the
  equivalent of `*ID*` or `*IX*` without editing the spreadsheet.
- `from_marker` defaults to `false`. **Only a `from_marker = true` row may modify an
  annotation**, which is what stops a stale saved file from suppressing an annotation you add
  to the workbook later.
- Renaming an annotated row makes the generated field name differ from the name written in the
  spreadsheet. The `codcel-io.toml` row is the record of that -- the annotation text in the
  workbook is never rewritten.

!!! note
    Selections live in `codcel-io.toml` rather than in [`codcel.toml`](./settings.md) because
    the desktop application's `codcel.toml` reader does not support TOML array-of-tables.

---

## Command Line

Three flags control the review step. Passing none of them means no configuration file is read
or written, and behaviour is identical to earlier versions of Codcel.

| Flag | Effect |
|------|--------|
| `--detect-io` | List the workbook's annotations plus the detected candidates, write them to the configuration file, then exit without transpiling |
| `--detect-io-interactive` | The same list, reviewed in an interactive terminal checklist, then transpile in the same run |
| `--io-config <PATH>` | Path to a `codcel-io.toml` to apply. Also chooses where `--detect-io` writes (default: `codcel-io.toml` next to the Excel file) |

### File-Based Flow

Best for scripted and CI use, where the configuration file is reviewed once and then committed.

```bash
# 1. Detect and write the candidate file
codcel \
  -e ./business_specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
  --table-path ./tables \
  --table-type parquet \
  --detect-io \
  --io-config ./codcel-io.toml

# 2. Edit ./codcel-io.toml -- toggle `selected`, rename `label`, set `field_option`

# 3. Transpile with your selections applied
codcel \
  -e ./business_specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
  --table-path ./tables \
  --table-type parquet \
  --io-config ./codcel-io.toml
```

`--detect-io` writes every entry it found with `selected = true`, including all of its
suggestions. Review the file before step 3 -- otherwise every suggestion is accepted.

If the path given to `--io-config` does not exist, Codcel prints a warning and continues,
generating from the workbook's annotations alone.

### Interactive Flow

```bash
codcel \
  -e ./business_specs/mortgage.xlsx \
  -p mortgage-calculator \
  -g ./generated \
  --table-path ./tables \
  --table-type parquet \
  --detect-io-interactive
```

- **Space** toggles an entry on or off, **Enter** confirms the selection
- You are then prompted to rename each selected label -- press Enter to keep the suggestion
- Transpilation continues automatically using your choices, and the configuration file is
  written so the same selections can be replayed non-interactively

---

## Desktop Application

1. Open a project and import an Excel file under **Business Specs**, as usual.
2. An **Inputs & Outputs** item appears in the sidebar once a spreadsheet has been imported.
   Open it.
3. The table lists the inputs and outputs configured in your spreadsheet with `*I*` and `*O*`
   annotations, each tagged with a **Marker** badge in the **Source** column. Auto-detection
   does not run on its own.

   | Column | What it shows |
   |--------|---------------|
   | **Include** | Tick or untick to include the entry in the generated code |
   | **Source** | `Marker` (from the spreadsheet) or `Detected` (a suggestion) |
   | **Type** | `Input` or `Output` |
   | **Cell** | The sheet and cell reference, as `Sheet1!B4` |
   | **Kind** | The cell's data kind: `Number`, `Formula`, `String`, `Boolean`, `DateTime` or `Time` |
   | **Option** | Inputs only: `Required`, `Default` or `Extra`. Outputs show a dash |
   | **Label** | Editable name for the generated field |

4. Click **Auto-detect** if you also want suggestions from unmarked cells. They are appended to
   the same table with a `Detected` badge, and your existing edits are kept.
5. Click **Reload from spreadsheet** after changing the `.xlsx` -- annotations and suggestions
   are re-read while your unsaved edits are preserved.
6. Click **Save selections** to write `codcel-io.toml` into the project folder. Reopening the
   view restores everything you saved, including any detected rows you accepted.
7. Go to **Generate Project** and generate as normal. Codcel picks up `codcel-io.toml` from the
   project folder automatically -- there is nothing further to configure.

The workbook is read off the user-interface thread, so the window stays responsive on large
workbooks.

---

## Limitations

- The analysis used to pick inputs and terminal outputs is a lightweight scan of formula text.
  It is intentionally approximate: it may miss defined names, `LAMBDA` functions, and structured
  or cross-sheet references, and it can occasionally over-suggest. It only affects *suggestions*
  that you review -- it never changes annotation behaviour or the correctness of generated code.
- Two annotation forms are **not** listed for review: combined outputs (an `*O*` naming several
  cells, such as `*O*A1,B4*Summary`) and CRUD tables (`*T*`). Both pass through untouched.
  Because combined outputs refer to cells rather than names, renaming an output does not disturb
  them.
- Range inputs such as `*I*A5:B25*Matrix` **are** listed, appearing once at the range's start
  cell.
- A workbook that is fully annotated correctly reports no candidates -- everything is already
  accounted for. The list still shows every annotation.

---

## See Also

- [Annotations](./annotations.md) -- the full `*I*` / `*O*` / `*T*` annotation reference
- [Command Line Interface](./cli.md) -- all CLI arguments
- [Desktop Application Guide](./desktop-app.md) -- the graphical workflow
- [Settings Reference](./settings.md) -- `codcel.toml` and project configuration
