<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Output Targets

Codcel generates production-ready code in multiple languages and frameworks. Each output target produces a complete, buildable project with its own build configuration, tests, and documentation.

The **Rust Calculation Library** is always generated and forms the foundation. All other targets either wrap the Rust engine (via JNI or FFI) or provide additional layers such as REST servers, web clients, and full-stack applications.

---

## How It Works

Codcel's code generation follows a layered architecture:

```
Excel Workbook
     |
     v
 Transpiler
     |
     +---> Rust Calculation Library (always generated)
     |         |
     |         +---> JNI Library (Java/Kotlin bridge)
     |         |         |
     |         |         +---> Java Calculation Library
     |         |         +---> Kotlin Calculation Library
     |         |
     |         +---> FFI Library (C-compatible bridge)
     |                   |
     |                   +---> C# Calculation Library
     |                   +---> Visual Basic Calculation Library
     |                   +---> Python Calculation Library
     |                   +---> Go Calculation Library
     |                   +---> Swift Calculation Library
     |
     +---> WASM Calculation Library (browser)
     +---> REST Servers (Rust, Java, Kotlin, C#, Go)
     +---> Web Clients (Rust, Java, Kotlin, C#, Python, Go, JS, TS, Swift)
     +---> Fullstack UI (Dioxus)
     +---> Command Line Tool
     +---> MCP Server (AI integration)
     +---> OpenAPI Document
```

---

## Target Categories

### [Calculation Libraries](./output-targets/calculation-libraries.md)
Standalone libraries for embedding calculations in your own applications. Available in Rust, WASM, Java, Kotlin, C#, Visual Basic, Python, Go, and Swift.

### [REST Servers](./output-targets/servers.md)
HTTP REST API servers that expose your calculations as web endpoints. Available in Rust, Java, Kotlin, C#, and Go.

### [Web Clients](./output-targets/web-clients.md)
Client libraries for calling the generated REST APIs. Available in Rust, Java, Kotlin, C#, Python, Go, JavaScript, TypeScript, and Swift.

### [Fullstack UI](./output-targets/fullstack-ui.md)
A complete web application with server and UI components, built with the Dioxus framework in Rust.

### [Integrations](./output-targets/integrations.md)
OpenAPI specifications, command-line tools, MCP servers for AI integration, and low-level JNI/FFI bindings.

---

## Selecting Output Targets

In the desktop app, open **Generate Project** from the sidebar and check the boxes for the targets you want. The Rust Calculation Library is always selected.

Some targets require a Codcel account. See [Authentication](./desktop-app.md#authentication) for details.

Output target selections are stored in the `[settings]` section of your `codcel.toml` file. See [Settings Reference](./settings.md#generation-settings) for the full list.

---

## Build Order

When building generated projects that depend on native libraries, follow this order:

1. **Build the Rust Calculation Library** -- `cargo build --release` in the calculation directory
2. **Build JNI or FFI** (if using Java, Kotlin, C#, VB, Python, Go, or Swift) -- `cargo build --release` in the `jni/` or `ffi/` directory
3. **Build the target-language library** -- using the target's build system (Gradle, .NET, Go, pip, Swift PM)
4. **Build the server** (if applicable) -- using the target's build system
5. **Build the web client** (if applicable)

The Fullstack UI, Command Line, and MCP Server targets are self-contained Rust projects that only need `cargo build --release`.

---

## Environment Variables

Several targets require the `CODCEL_TABLE_PATH` environment variable to locate table data files:

```bash
export CODCEL_TABLE_PATH=../../tables/
```

This applies to: Go, Swift, C#, Visual Basic, and the MCP Server.

### Runtime Formatting

All generated targets support runtime locale detection and `CODCEL_*` environment variable overrides for formatting (decimal separator, currency symbol, thousands separator, and more). REST servers also accept the `Accept-Language` HTTP header, and calculation libraries provide per-call language override APIs.

See [Runtime Formatting](./runtime-formatting.md) for full details.