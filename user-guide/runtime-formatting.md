<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Runtime Formatting

Codcel's formatting settings (decimal separator, currency symbol, thousands separator, etc.) are configured at code generation time via `codcel.toml` or the CLI. These become the **default** formatting for the generated code.

At runtime, the generated code can also detect and apply locale-appropriate formatting automatically. This is useful for multi-tenant applications, internationalised services, and deployments where the runtime locale differs from the build machine.

---

## How It Works

Runtime formatting uses a three-tier resolution order. Each tier can override the one before it:

1. **OS locale detection** -- the generated code detects the operating system's locale at startup and applies appropriate formatting (decimal separator, currency symbol, thousands separator, language)
2. **Environment variable overrides** -- `CODCEL_*` environment variables override individual formatting fields
3. **Per-call override** -- API variants accept a language tag (e.g. `"de"`, `"fr-FR"`) to override formatting for a single calculation call

The final formatting used for a calculation is determined by whichever tier provides the most specific value.

---

## Environment Variables

The following environment variables override formatting at runtime. They take effect when the generated code starts (or when a calculation is invoked, depending on the target).

| Variable | Description | Example |
|----------|-------------|---------|
| `CODCEL_DECIMAL_SEPARATOR` | Decimal point character | `,` |
| `CODCEL_CURRENCY_SYMBOL` | Currency symbol | `€` |
| `CODCEL_THOUSANDS_SEPARATOR` | Thousands grouping character | `.` |
| `CODCEL_USE_EXCEL_ROUNDING` | Use Excel's 15-digit rounding (`true`/`false`) | `true` |
| `CODCEL_LANGUAGE` | Language code for locale detection | `de` |
| `CODCEL_ALLOW_LOTUS_1_2_3_1900_DATE_BUG` | Replicate Excel's 1900 date bug (`true`/`false`) | `true` |
| `CODCEL_USE_PORTABLE_MATH` | Use portable pure-Rust math for cross-platform determinism (`true`/`false`) | `false` |

### Example

```bash
# Run a Rust server with German formatting
CODCEL_DECIMAL_SEPARATOR="," \
CODCEL_THOUSANDS_SEPARATOR="." \
CODCEL_CURRENCY_SYMBOL="€" \
CODCEL_LANGUAGE="de" \
./target/release/my-project-server
```

```bash
# Run a Python calculation with French formatting
export CODCEL_DECIMAL_SEPARATOR=","
export CODCEL_THOUSANDS_SEPARATOR=" "
export CODCEL_CURRENCY_SYMBOL="€"
export CODCEL_LANGUAGE="fr"
python3 -m my_project
```

Environment variables override OS locale detection but are themselves overridden by per-call language parameters.

---

## Accept-Language Header (REST Servers)

All generated REST servers automatically extract the `Accept-Language` HTTP header from incoming requests. When present, the server uses the primary language tag to apply locale-appropriate formatting for that specific request.

```
POST /monthly_payment
Content-Type: application/json
Accept-Language: de

{
  "interest_rate": 5.5,
  "loan_amount": 250000,
  "term_years": 30
}
```

When the `Accept-Language` header is:
- **Present** -- the server resolves formatting from the language tag, with environment variable overrides still applied on top
- **Absent** -- the server uses the default formatting (OS locale + environment variables)

This is supported in all generated servers: **Rust**, **Java**, **Kotlin**, **C#**, **Go**, and the **Fullstack UI** (Dioxus).

The **Fullstack UI** automatically sends the browser's preferred language (`navigator.language`) as the `Accept-Language` header on every API call.

### OpenAPI

The generated OpenAPI specification includes the `Accept-Language` header as an optional parameter on every endpoint:

```json
{
  "name": "Accept-Language",
  "in": "header",
  "required": false,
  "description": "Language tag (e.g. de, fr-FR, en-US)",
  "schema": {
    "type": "string",
    "example": "en-US"
  }
}
```

---

## Per-Call Language Override (Calculation Libraries)

Each generated calculation library provides a `_with_language` variant that accepts a language tag string. This allows you to override formatting on a per-call basis without modifying environment variables or server configuration.

### Rust

```rust
use codcel_calculation_engine::value_format::ValueFormat;

// Default formatting (OS locale + env vars)
let result = calculate_monthly_payment(&input).await;

// With full ValueFormat override
let vf = ValueFormat::from_language_with_env("de");
let result = calculate_monthly_payment_with_format(&input, vf).await;
```

### Java

```java
// Default formatting
var result = Calculation.monthlyPayment(input);

// With language override
var result = Calculation.monthlyPaymentWithLanguage(input, "de");
```

### Kotlin

```kotlin
// Default formatting
val result = Calculation.monthlyPayment(input)

// With language override
val result = Calculation.monthlyPaymentWithLanguage(input, "de")
```

### C\#

```csharp
// Default formatting
var result = calculation.Calculate(input);

// With language override
var result = calculation.WithLanguage(input, "de");
```

### Python

```python
# Default formatting
result = monthly_payment(input)

# With language override
result = monthly_payment_with_language(input, "de")
```

### Go

```go
// Default formatting
result, err := calculation.MonthlyPayment(input)

// With language override
result, err := calculation.MonthlyPaymentWithLanguage(input, "de")
```

### Swift

```swift
let calculator = MonthlyPayment()

// Default formatting
let result = try calculator.calculate(input: input)

// With language override
let result = try calculator.calculateWithLanguage(input: input, language: "de")
```

---

## Supported Languages

The following language codes are recognised for automatic locale detection. When a language tag includes a region (e.g. `fr-FR`), the primary language is extracted.

| Languages | Decimal | Thousands | Currency |
|-----------|---------|-----------|----------|
| `en` | `.` | `,` | `$` |
| `de`, `it`, `es`, `nl`, `ro`, `hr`, `sl`, `el`, `tr` | `,` | `.` | `€` |
| `fr`, `pl`, `cs`, `sv`, `fi`, `hu`, `sk`, `et`, `lv`, `lt` | `,` | ` ` (space) | `€` |
| `pt` | `,` | `.` | `R$` |
| `ja`, `zh`, `ko` | `.` | `,` | `¥` |
| `ru`, `uk`, `be`, `kk`, `ky` | `,` | ` ` (space) | `₽` |
| `ar`, `fa`, `ur` | `.` | `,` | `﷼` |
| `hi`, `bn`, `ta`, `te`, `mr`, `gu`, `kn`, `ml` | `.` | `,` | `₹` |
| `th` | `.` | `,` | `฿` |
| `vi` | `,` | `.` | `₫` |
| `he`, `iw` | `.` | `,` | `₪` |
| `da`, `nb`, `nn`, `no`, `is` | `,` | `.` | `kr` |

Unrecognised language codes fall back to the default formatting from code generation.

---

## WASM (WebAssembly)

In WebAssembly targets, OS locale detection is not available (the browser sandbox does not expose system locale information). The generated WASM code uses the formatting defaults from code generation.

To use locale-specific formatting in WASM:

- Use the `_with_format` API variant to pass a `ValueFormat` directly from JavaScript
- Set `CODCEL_*` environment variables before building (they are baked in at compile time for WASM)

For browser-based applications, the **Fullstack UI** target is recommended -- it runs calculations on the server where full locale detection is available, and the browser's language is forwarded automatically via the `Accept-Language` header.

---

## MCP Server

The MCP server uses stdio transport (not HTTP), so there is no `Accept-Language` header. Formatting is controlled entirely by:

1. OS locale detection at process startup
2. `CODCEL_*` environment variables set in the MCP server configuration

```json
{
  "mcpServers": {
    "my-project": {
      "command": "/path/to/my-project-mcp-server",
      "env": {
        "CODCEL_TABLE_PATH": "/path/to/tables/",
        "CODCEL_LANGUAGE": "de",
        "CODCEL_DECIMAL_SEPARATOR": ",",
        "CODCEL_THOUSANDS_SEPARATOR": ".",
        "CODCEL_CURRENCY_SYMBOL": "€"
      }
    }
  }
}
```

---

## Relationship to Build-Time Settings

The formatting settings in `codcel.toml` and the CLI (`--decimal-separator`, `--currency-symbol`, etc.) control the **default** formatting baked into the generated code. Runtime formatting does not replace these -- it adds the ability to override them at runtime.

| Concern | Configured via |
|---------|----------------|
| Default formatting for generated code | `codcel.toml` / CLI flags |
| Runtime OS locale detection | Automatic (no configuration needed) |
| Runtime environment overrides | `CODCEL_*` environment variables |
| Per-request formatting (servers) | `Accept-Language` HTTP header |
| Per-call formatting (libraries) | `_with_language` / `_with_format` API variants |

See [Settings Reference](./settings.md) for build-time formatting configuration.