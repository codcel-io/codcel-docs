<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

# Runtime Formatting

Codcel's formatting settings (decimal separator, currency symbol, thousands separator, etc.) are configured at code generation time via `codcel.toml` or the CLI. These become the **default** formatting for the generated code.

At runtime, the generated code can also detect and apply locale-appropriate formatting automatically. This is useful for multi-tenant applications, internationalised services, and deployments where the runtime locale differs from the build machine.

---

## How It Works

Runtime formatting uses a three-tier resolution order. Each tier can override the one before it:

1. **OS locale detection** -- the generated code detects the operating system's locale at startup and applies appropriate formatting (decimal separator, currency symbol, thousands separator, language, region)
2. **Environment variable overrides** -- `CODCEL_*` environment variables override individual formatting fields
3. **Per-call override** -- API variants accept a language tag (e.g. `"de"`, `"fr-FR"`) to override formatting for a single calculation call

The final formatting used for a calculation is determined by whichever tier provides the most specific value.

### What the language and region each decide

The two subtags of a tag like `en-GB` govern different things, and Codcel keeps them in separate fields for that reason.

- The **language** decides names: month and weekday names for `TEXT(date, "mmmm")` and `"dddd"`, AM/PM markers, and the error values a localised deployment shows.
- The **region** decides conventions: the decimal and thousands separators, the currency symbol, and which built-in date format Excel means. Excel renders the same built-in short date as `dd/mm/yyyy` for `en-GB` and `m/d/yy` for `en-US`.

So `en-DE` -- an English speaker working in Germany -- gets English month names with German number separators, which is what Excel does.

Names, symbols and calendar data come from [Unicode CLDR](https://cldr.unicode.org/). The three settings you can override -- decimal separator, thousands separator and currency symbol -- are Codcel's own and always win over the CLDR values.

---

## Environment Variables

The following environment variables override formatting at runtime. They take effect when the generated code starts (or when a calculation is invoked, depending on the target).

| Variable | Description | Example |
|----------|-------------|---------|
| `CODCEL_DECIMAL_SEPARATOR` | Decimal point character | `,` |
| `CODCEL_CURRENCY_SYMBOL` | Currency symbol | `€` |
| `CODCEL_THOUSANDS_SEPARATOR` | Thousands grouping character | `.` |
| `CODCEL_USE_EXCEL_ROUNDING` | Use Excel's 15-digit rounding (`true`/`false`) | `true` |
| `CODCEL_LANGUAGE` | Language tag for locale detection. A full tag sets the region too | `de` or `en-GB` |
| `CODCEL_REGION` | Region subtag on its own, when the language is set separately | `CH` |
| `CODCEL_TIMEZONE` | IANA timezone for `NOW` and `TODAY`. Unset means the host's local zone | `Europe/Berlin` |
| `CODCEL_MOCK_NOW` | Freeze the clock at a fixed RFC 3339 instant, for tests. An unparseable value is ignored | `2024-12-03T18:00:00Z` |
| `CODCEL_ALLOW_LOTUS_1_2_3_1900_DATE_BUG` | Replicate Excel's 1900 date bug (`true`/`false`). Disabling this re-bases the serial system rather than correcting dates — see [Date Handling](./differences/date-handling.md) | `true` |
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

Three behaviours differ inside a WebAssembly sandbox and are worth knowing before you rely on them:

- **Locale detection is unavailable, and `CODCEL_*` overrides are ignored.** The sandbox exposes
  no system locale, and environment variables cannot be read at runtime, so the `CODCEL_*`
  variables listed above have no effect on a WASM build. `ValueFormat` falls back to the values
  supplied by the caller. Use the `_with_format` API variant to pass a `ValueFormat` directly from
  JavaScript if you need particular separators or a currency symbol; otherwise the defaults baked
  in at code generation apply.
- **`NOW()` and `TODAY()` require a JavaScript host.** They resolve the current time through
  `js_sys::Date`. Browser and Node hosts via `wasm-bindgen` satisfy this; a bare runtime such as
  Wasmtime does not.
- **`RAND()` and `RANDBETWEEN()` are deterministic.** There is no entropy source in the sandbox,
  so every instance produces the same sequence. This matters for any simulation or Monte Carlo
  work.

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

---

## Timezones: `NOW` and `TODAY`

`NOW()` and `TODAY()` read the **local wall clock**, as Excel does. A spreadsheet opened in Auckland at nine in the morning shows that day's date, and so does the same spreadsheet opened in Los Angeles at nine in the morning thirteen hours later. Excel has no timezone concept at all -- a date serial is a zoneless wall-clock reading.

By default the generated code reads the host machine's zone. Set `CODCEL_TIMEZONE` (or `--timezone` at transpile time) to pin a specific IANA zone instead:

```bash
CODCEL_TIMEZONE="Europe/Berlin" ./my-project-server
```

!!! warning "This changed in engine 0.1.10"
    Earlier versions returned UTC from both functions. For a caller at UTC+13 that is yesterday's date for thirteen hours of every day, and for one at UTC-8 it rolls over to tomorrow eight hours early. If a deployment was relying on the UTC behaviour, set `CODCEL_TIMEZONE="UTC"` to keep it.

### Freezing the clock in tests

A workbook containing a `TODAY()` or `NOW()` cell generates a test asserting the value from the day the workbook was saved, so it only passes on that date. Set `CODCEL_MOCK_NOW` to the save date and the test becomes deterministic:

```bash
CODCEL_MOCK_NOW="2024-12-03T18:00:00Z" cargo test --release
```

The value must be RFC 3339 including an offset -- `2024-12-03T18:00:00Z`, not `2024-12-03T18:00:00`. An unparseable value is ignored and the real clock is used, so a stray variable cannot take a calculation down.

---

## WebAssembly builds

Generated wasm crates are built with the calculation engine's `named-timezones` feature **off**. That feature embeds the IANA timezone database, which costs roughly 890 KB of the wasm bundle once anything reaches for it.

Turning it off does not make `NOW` and `TODAY` return UTC -- they still read the browser's local clock. It only removes the ability to pin an explicitly named zone through `CODCEL_TIMEZONE`, which a browser has no business overriding anyway.

The CLDR locale table adds about 82 KB and is kept on, since it is what localised formatting needs.

---

## Web clients

Every generated REST server derives a per-request format from the `Accept-Language` header, and every generated web client now sends one:

- The **TypeScript** and **JavaScript** clients send `navigator.language`, so a German visitor sees `1.234,56` where an American sees `1,234.56`.
- The **Python, Go, Java, Kotlin, C# and Rust** clients send `CODCEL_LANGUAGE` when it is set. These usually run on a server, whose own locale says nothing about who the answer is for, so nothing is sent unless you ask for it.

With no header, the server falls back to the locale the project was transpiled with.
