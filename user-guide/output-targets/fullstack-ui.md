<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Fullstack UI

The Fullstack UI target generates a complete web application with both server and client components, built using the [Dioxus](https://dioxuslabs.com/) framework in Rust. It provides a ready-to-use web interface for interacting with your calculations.

---

## Prerequisites

- **Rust toolchain** (stable)
- **Dioxus CLI:** Install with `cargo install dioxus-cli`

---

## Project Structure

```
fullstack-ui/
├── Cargo.toml          # Rust dependencies
├── Dioxus.toml         # Dioxus configuration
├── src/
│   ├── main.rs         # Application entry point
│   ├── route.rs        # Page routes
│   ├── components/     # Reusable UI components
│   └── backend/        # Server-side logic
└── assets/             # Static assets (CSS, images)
```

---

## Development

For development with hot reloading:

```bash
dx serve
```

This starts a development server (default port 8080) that automatically rebuilds when you change files.

---

## Production Build

```bash
cargo build --release
```

Run the compiled binary:

```bash
./target/release/<project-name>
```

The application serves both the API and the web interface on port 8080.

---

## UI Configuration from Excel

You can customise the generated UI by adding special configuration sheets to your Excel workbook:

- **`codcel-ui-language`** -- multi-language labels for inputs and outputs
- **`codcel-ui-options`** -- map inputs to outputs for grouping
- **`codcel-ui-layouts`** -- control widget types (text, slider, dropdown) and layout

For full details, see [UI Configuration](../ui-configuration.md).

---

## Locale-Aware Formatting

The Fullstack UI automatically sends the browser's preferred language (`navigator.language`) as the `Accept-Language` header on every API call. The server uses this to apply locale-appropriate number and currency formatting for the response.

No additional configuration is needed -- the user's browser language is detected and forwarded transparently. See [Runtime Formatting](../runtime-formatting.md) for details.

---

## Features

- Server-side rendering with client-side hydration
- Responsive web design
- Input forms generated from your Excel annotations
- Real-time calculation results
- Locale-aware formatting based on browser language
- CORS support for external API access
- Built-in testing tools for running and creating CSV-based tests

---

## Testing Tools

The Fullstack UI includes built-in testing tools accessible from the **Tests** button in the top right of the application. These let you run and create tests directly in the browser — no code required. Everything runs locally.

- **Run Tests** — upload a CSV with inputs and optional expected outputs to verify calculations
- **Create Tests** — define input ranges (min, max, step) and Codcel generates all combinations automatically

For full details, see [Testing and Validation](../testing.md#testing-with-the-fullstack-ui).