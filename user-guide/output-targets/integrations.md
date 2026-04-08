<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Integrations

Codcel generates several integration targets for API documentation, command-line tools, AI assistants, and low-level language bindings.

---

## OpenAPI Document

Generates an OpenAPI 3.0.3 specification file (`open-api.json`) describing your REST API.

- **Format:** JSON
- **Use with:** Swagger UI, Postman, Redoc, or any OpenAPI-compatible tool
- **Content:** All endpoints, request/response schemas, server URLs

The specification includes server URLs for each generated server:

| Server | Default URL |
|--------|-------------|
| Rust | `http://localhost:3030` |
| Java | `http://localhost:7000` |
| Kotlin | `http://localhost:8000` |
| C# | `http://localhost:5000` |
| Go | `http://localhost:8080` |

---

## Command Line Tool

Generates a CLI tool for running calculations from the terminal.

- **Build system:** Cargo
- **Build:** `cargo build --release`
- **Binary:** `<project-name>-cli`

### Usage

Run a calculation with inline JSON:

```bash
./target/release/<project-name>-cli --calc monthly_payment --input '{"interest_rate": 5.5, "loan_amount": 250000, "term_years": 30}' --pretty
```

Read input from a file:

```bash
./target/release/<project-name>-cli --calc monthly_payment --input @input.json
```

Read input from stdin:

```bash
echo '{"interest_rate": 5.5}' | ./target/release/<project-name>-cli --calc monthly_payment --input -
```

Output is always JSON. Use `--pretty` for formatted output.

---

## MCP Server

Generates a [Model Context Protocol](https://modelcontextprotocol.io/) server, allowing AI assistants like Claude to call your calculations as tools.

- **Build system:** Cargo
- **Build:** `cargo build --release`
- **Binary:** `<project-name>-mcp-server`

### Configuration in Claude Desktop

Add the MCP server to your Claude Desktop configuration file:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "my-project": {
      "command": "/path/to/target/release/<project-name>-mcp-server",
      "env": {
        "CODCEL_TABLE_PATH": "/path/to/tables/"
      }
    }
  }
}
```

### Formatting

The MCP server uses stdio transport (no HTTP headers), so formatting is controlled via OS locale detection and `CODCEL_*` environment variables set in the MCP configuration. See [Runtime Formatting](../runtime-formatting.md#mcp-server) for details.

### Defining MCP Tools in Excel

You define the MCP tools, parameters, and results in the `codcel-mcp` configuration sheet in your Excel workbook. See [UI Configuration](../ui-configuration.md#mcp-configuration-codcel-mcp) for details.

---

## JNI (Java Native Interface)

Generates a Rust library with JNI bindings, allowing Java and Kotlin code to call the Rust calculation engine directly.

- **Build system:** Cargo
- **Build:** `cargo build --release`
- **Output:** Dynamic library (`.so` on Linux, `.dylib` on macOS, `.dll` on Windows)

The JNI library is a dependency of the Java and Kotlin calculation libraries and servers. Build it before building any Java or Kotlin target.

---

## FFI (Foreign Function Interface)

Generates a C-compatible dynamic library that can be loaded by any language with C FFI support.

- **Build system:** Cargo
- **Build:** `cargo build --release`
- **Output:** Dynamic library (`.so` on Linux, `.dylib` on macOS, `.dll` on Windows)

The FFI library is used by C#, Visual Basic, Python, Go, and Swift calculation libraries. Build it before building any of those targets.

Both JNI and FFI libraries include `_with_language` function variants that accept a language tag for per-call locale-specific formatting. See [Runtime Formatting](../runtime-formatting.md) for details.

---

## Build Order for Integration Targets

| Target | Depends On |
|--------|------------|
| OpenAPI Document | None (generated directly) |
| Command Line | Rust Calculation Library |
| MCP Server | Rust Calculation Library |
| JNI | Rust Calculation Library |
| FFI | Rust Calculation Library |
| Excel Python Interface | FFI Library, Python Calculation Library |
| Excel Web Client Python Interface | Python Web Client, running REST Server |