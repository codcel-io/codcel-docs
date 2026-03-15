<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Codcel Desktop Application

The Codcel Desktop application is the primary tool for transforming Excel spreadsheets into production-ready software. It runs entirely on your local machine and is available for **Windows**, **macOS**, and **Linux**.

Download the latest version from [codcel.io](https://codcel.io).

---

## First Launch and Onboarding

When you open Codcel for the first time, an onboarding wizard guides you through the initial setup:

1. **Welcome** -- an introduction to Codcel
2. **Quick Start** -- a brief overview of the workflow
3. **Projects Location** -- select a default directory where your Codcel projects will be stored

The projects location is saved to your user configuration (`~/codcel.toml`) and is used as the default directory when creating or opening projects. You can change it later from the Home page.

After completing the onboarding, you will not see it again on subsequent launches.

---

## Home Page

The Home page is the first screen you see after onboarding. It presents two options:

### Create a New Project

1. Click the **Create** button
2. Enter a **project name** in the dialog that appears
3. Select a **directory** for the project (defaults to your configured projects location)
4. Click **Create Project**

Codcel creates a new folder with the project name inside the selected directory and initialises a `codcel.toml` configuration file.

### Open an Existing Project

1. Click the **Open** button
2. Browse to the folder of an existing Codcel project
3. Click **Open Project**

Codcel looks for a `codcel.toml` file in the selected directory to confirm it is a valid project. If the file is not found, an error message is shown.

The version number is displayed in the bottom-left corner of the Home page.

---

## Project Dashboard

After creating or opening a project, you enter the **Project Dashboard**. This is where you do all your work: importing files, configuring settings, and generating code.

### Navigation

The dashboard uses a **drawer-based sidebar** for navigation. Click the menu button (three horizontal lines) in the top-right corner to open the sidebar.

The sidebar contains the following items:

**Always visible:**
- **Business Specs** -- import and manage your Excel files
- **Settings** -- configure formatting and calculation options

**Visible after importing Excel files:**
- **Generate Project** -- select output targets and generate code

**Visible after generating code** (one entry per enabled output type):
- Rust Calculation Library, Rust Model Library, Tables
- WASM Calculation Library, Fullstack UI, RESTful Server
- Web Clients (Rust, Java, Kotlin, C#, Python, Go, JavaScript, TypeScript, Swift)
- Calculation Libraries (Java, Kotlin, C#, Visual Basic, Python, Go, Swift)
- RESTful Servers (Java, Kotlin, C#, Go)
- OpenAPI Document, Command Line, MCP Server, JNI, FFI Library

Each output-type entry in the sidebar links to a view where you can inspect the generated source code for that target.

### Tutorial Overlay

The first few times you open a project, a brief tutorial overlay highlights the key areas of the dashboard. You can dismiss the tutorial or choose not to see it again.

---

## Importing Excel Files

The **Business Specs** view is where you import your Excel spreadsheets.

### How to Import

You can import files in two ways:

- **Drag and drop** files directly into the import area
- **Click Browse** to open a file picker

### Supported Formats

| Format | Extension | Recommendation |
|--------|-----------|----------------|
| Excel Workbook | `.xlsx` | **Recommended** -- best compatibility |
| Excel 97-2003 Workbook | `.xls` | Supported -- older format with fewer features |
| Excel Macro-Enabled Workbook | `.xlsm` | Supported -- macros/VBA are ignored |
| Excel Binary Workbook | `.xlsb` | Supported -- may have parsing limitations for complex workbooks |
| Excel Add-In | `.xla` | Supported |
| Excel Macro-Enabled Add-In | `.xlam` | Supported -- macros/VBA are ignored |
| OpenDocument Spreadsheet | `.ods` | Supported |

**Notes:**
- **`.xlsx` is recommended** for best compatibility and most reliable parsing
- **Macros and VBA** are not transpiled -- Codcel reads formula logic only, not macro code
- **`.xlsb`** (binary format) is supported but `.xlsx` is preferred for complex workbooks
- **`.xls`** (legacy format) supports fewer modern Excel features

### What Happens on Import

When you import a file:

1. The file is copied into the `business_specs/` subdirectory of your project
2. A progress indicator shows the copy status
3. The file is registered in the `[files]` section of `codcel.toml`
4. The **Generate Project** option becomes available in the sidebar

You can import multiple files. After importing, you can view the list of imported files and open the `business_specs/` folder in your system's file explorer.

For guidance on preparing your Excel files before import, see the [Excel Guidelines](./codcel-excel-guidelines.md).

---

## Configuring Settings

Open the **Settings** view from the sidebar to configure how Codcel interprets your Excel data and generates code.

Settings are saved per project in the `codcel.toml` file. Click **Save** to persist your changes.

For a full reference of all available settings, see the [Settings Reference](./settings.md).

### Key Settings

- **Decimal Separator** and **Thousands Separator** -- control number formatting to match your locale
- **Currency Symbol** -- set the currency symbol used in generated code
- **Use Excel Rounding** -- enable Excel-compatible rounding behaviour (15 significant digits)
- **Strict Type Conversion** -- control how Codcel handles implicit type conversions
- **Enable Iterative Calculation** -- allow circular references to be resolved iteratively, with configurable maximum iterations and convergence threshold

---

## Generating Code

Once you have imported at least one Excel file, the **Generate Project** view becomes available in the sidebar.

### Selecting Output Targets

The Generate Project view displays a list of checkboxes for each output target. The **Rust Calculation Library** is always selected and cannot be disabled -- it forms the core of all generated projects.

Additional output targets are grouped into categories such as:

- **Servers** -- REST APIs in Rust, Java, Kotlin, C#, Go
- **Web Clients** -- client libraries in multiple languages
- **Calculation Libraries** -- standalone calculation code in Java, Python, C#, and more
- **Full-Stack** -- complete web applications with UI
- **Integration** -- OpenAPI specs, CLI tools, MCP servers, JNI/FFI bindings

Some output targets require you to be logged in with a Codcel account.

### Running the Generation

1. Select the output targets you want
2. Click **Generate**
3. A progress bar shows the generation status
4. When complete, the generated code appears in your project directory

After generation completes, new entries appear in the sidebar for each enabled output type, where you can view and inspect the generated source code.

---

## Authentication

Codcel can be used without an account for generating the core Rust Calculation Library. To access additional output targets, you need to log in.

### Logging In

1. Click the **Login** button in the header bar
2. Enter your email address
3. Click **Send Magic Link**
4. Check your email and click the verification link
5. Return to the Codcel app and click **Complete**

Your session is maintained securely. Access tokens are stored in memory and refresh tokens are stored in your operating system's secure keychain. Your session refreshes automatically in the background.

### Logging Out

Click the user menu in the header and select **Logout**. When you log out, any premium output targets you had selected will be deselected.

---

## Theme and Language

### Themes

Codcel supports multiple visual themes including both light and dark options. Click the **theme selector** in the header to browse and switch themes.

### Language

The user interface is available in 10 languages:

| Language | Code |
|----------|------|
| English | `en` |
| Spanish | `es` |
| Portuguese | `pt` |
| French | `fr` |
| German | `de` |
| Bulgarian | `bg` |
| Italian | `it` |
| Japanese | `ja` |
| Korean | `ko` |
| Chinese | `zh` |

You can change the UI language from the application settings. The language preference is stored in your global configuration file (`~/codcel.toml`).

---

## Project File Structure

After creating a project and generating code, your project directory will contain:

```
my-project/
├── codcel.toml              # Project configuration
├── business_specs/          # Imported Excel files
│   └── spreadsheet.xlsx
├── src/                     # Generated Rust source code
└── generated/               # Generated projects for other languages
    ├── rust-calculation/
    ├── java-calculation/
    ├── web-client/
    └── ...
```

The `codcel.toml` file contains all project settings, file references, and generation options. For details on its structure, see the [Settings Reference](./settings.md).

---

## Next Steps

- [Preparing Excel Files](./codcel-excel-guidelines.md) -- guidelines for cleaning and annotating your spreadsheets
- [Excel to Code Walkthrough](./excel-to-code.md) -- step-by-step guide from spreadsheet to generated project
- [Settings Reference](./settings.md) -- detailed explanation of all configuration options
- [UI Configuration](./ui-configuration.md) -- configuring generated UI elements from within Excel