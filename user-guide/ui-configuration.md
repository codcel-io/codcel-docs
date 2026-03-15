<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# UI Configuration

Codcel can generate user interfaces (via the Fullstack UI output target) that allow users to interact with your calculations through a web application. You can configure these generated UIs directly from within your Excel workbook by adding special configuration sheets.

---

## Configuration Sheets

Codcel recognises three special sheet names for UI configuration and one for MCP (Model Context Protocol) integration:

| Sheet Name | Purpose |
|------------|---------|
| `codcel-ui-language` | Multi-language translations for UI labels |
| `codcel-ui-options` | Input-to-output name mappings |
| `codcel-ui-layouts` | Widget type and layout configuration |
| `codcel-mcp` | MCP tool definitions for AI integration |

These sheets are processed during code generation and are not included in the calculation logic. They are optional -- if they are not present, Codcel uses sensible defaults.

---

## Language Configuration (`codcel-ui-language`)

The `codcel-ui-language` sheet allows you to provide translations for input and output labels in the generated UI, enabling multilingual applications.

### Sheet Structure

| | A | B | C | D |
|---|---|---|---|---|
| **1** | *(ID)* | en | fr | de |
| **2** | interest_rate | Interest Rate | Taux d'intérêt | Zinssatz |
| **3** | loan_amount | Loan Amount | Montant du prêt | Darlehensbetrag |
| **4** | monthly_payment | Monthly Payment | Paiement mensuel | Monatliche Zahlung |

- **Column A** contains the translation IDs (typically matching your input/output names)
- **Row 1** contains locale codes (e.g. `en`, `fr`, `de`, `es`, `pt`, `ja`)
- **Each cell** contains the translated label for that ID in the corresponding locale

The generated UI will display labels in the user's selected language, falling back to the first available translation if a language is not defined.

---

## Options Configuration (`codcel-ui-options`)

The `codcel-ui-options` sheet maps input names to output names, defining which inputs feed into which outputs in the generated UI. This controls how the UI groups and presents calculation inputs alongside their results.

### Sheet Structure

| | A | B |
|---|---|---|
| **1** | Input | Output |
| **2** | Interest Rate | Monthly Payment |
| **3** | Loan Amount | Monthly Payment |
| **4** | Term Years | Monthly Payment |

- **Column A** contains the input name (as labelled in your spreadsheet)
- **Column B** contains the output name that the input is associated with

Names are automatically converted to snake_case internally. This mapping tells the generated UI which input fields to display alongside each output calculation.

---

## Layouts Configuration (`codcel-ui-layouts`)

The `codcel-ui-layouts` sheet controls the visual layout and widget types used in the generated UI. You can specify how each input is rendered (as a text field, slider, dropdown, etc.) and how inputs are grouped.

### Sheet Structure

| | A | B | C |
|---|---|---|---|
| **1** | Output | Widget | Name |
| **2** | monthly_payment | group | Loan Details |
| **3** | monthly_payment | slider | interest_rate |
| **4** | monthly_payment | text | loan_amount |
| **5** | monthly_payment | dropdown | term_years |

- **Column A** contains the output name (the calculation this layout applies to)
- **Column B** contains the widget type
- **Column C** contains the input name or group label

### Widget Types

| Widget | Description |
|--------|-------------|
| `group` | A visual grouping header. The **Name** column contains the group's display label (not converted to snake_case) |
| `text` | A standard text input field |
| `slider` | A range slider input |
| `dropdown` | A dropdown/select menu |

Multiple layouts can be defined for the same output. Input widgets listed after a `group` entry are visually grouped under that heading in the generated UI.

---

## MCP Configuration (`codcel-mcp`)

The `codcel-mcp` sheet defines tools, parameters, and results for generating an MCP (Model Context Protocol) server. This enables AI assistants to interact with your calculations as tools.

### Sheet Structure

| | A | B | C | D |
|---|---|---|---|---|
| **1** | Type | Tool | Name | Description |
| **2** | tool | Calculate Mortgage | Calculate Mortgage | Calculates monthly mortgage payments based on loan parameters |
| **3** | parameter | Calculate Mortgage | Interest Rate | The annual interest rate as a percentage |
| **4** | parameter | Calculate Mortgage | Loan Amount | The total loan amount in currency units |
| **5** | parameter | Calculate Mortgage | Term Years | The loan term in years |
| **6** | result | Calculate Mortgage | Monthly Payment | The calculated monthly payment amount |

- **Column A** (`Type`) -- one of `tool`, `parameter`, or `result`
- **Column B** (`Tool`) -- the tool name that this row belongs to
- **Column C** (`Name`) -- the parameter or result name (for `tool` rows, this repeats the tool name)
- **Column D** (`Description`) -- a human-readable description

### Row Types

| Type | Purpose |
|------|---------|
| `tool` | Defines a new tool. Must appear before any parameters or results for that tool |
| `parameter` | Defines an input parameter for a tool |
| `result` | Defines an output result for a tool |

All rows must have values in all four columns. Incomplete rows generate a warning and are skipped. Tool names and parameter/result names are automatically converted to snake_case internally.

The generated MCP server exposes each defined tool as an MCP tool that AI assistants (such as Claude) can call. Parameters become the tool's input schema and results define the output structure.

---

## Notes

- Sheet names are case-insensitive (`codcel-ui-language` and `CODCEL-UI-LANGUAGE` are treated the same)
- All names are converted to snake_case internally for code generation
- Configuration sheets are only processed when the corresponding output target is enabled (e.g. Fullstack UI, MCP Server)
- If you include a configuration sheet but do not enable its output target, the sheet is ignored
- For best results, ensure that the names used in configuration sheets match the input and output names defined in your spreadsheet's formulas