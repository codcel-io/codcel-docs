<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# REST Servers

Codcel generates REST API servers that expose your Excel calculations as HTTP endpoints. Each calculation method becomes a `POST` endpoint that accepts JSON input and returns JSON output.

---

## Rust Server

- **Build system:** Cargo
- **Framework:** Axum
- **Build:** `cargo build --release`
- **Run:** `cargo run`
- **Default port:** 3030
- **Dependencies:** axum, tokio, serde, tower-http (CORS)

The Rust server is the recommended option for production deployments. It has the smallest footprint and best performance.

---

## Java Server

- **Build system:** Gradle
- **Framework:** Javalin 6
- **Prerequisites:** JDK 11+
- **Build:** `./gradlew build`
- **Run:** `./gradlew run`
- **Default port:** 7000
- **Custom port:** `./gradlew run -Pport=8080`
- **Bridge:** JNI -- requires the JNI library to be built first

---

## Kotlin Server

- **Build system:** Gradle with Kotlin plugin
- **Framework:** Javalin 6
- **Prerequisites:** JDK 17+ (toolchain 21 configured)
- **Build:** `./gradlew build`
- **Run:** `./gradlew run`
- **Default port:** 7000
- **Custom port:** `./gradlew run -Pport=8080`
- **Bridge:** JNI -- requires the JNI library to be built first

---

## C# Server

- **Build system:** .NET 8.0 (ASP.NET Core)
- **Prerequisites:** .NET 8 SDK
- **Run:** `dotnet run -p:CodcelTargetOS=<os>`
- **Custom port:** `dotnet run --urls http://localhost:8000 -p:CodcelTargetOS=<os>`
- **OS parameter:** `linux`, `macos`, or `windows`
- **Bridge:** FFI -- requires the FFI library to be built first

---

## Go Server

- **Build system:** Go Modules
- **Framework:** Gorilla Mux
- **Prerequisites:** Go 1.21+; TDM-GCC on Windows (for CGO)
- **Build/Run:** `go run .`
- **Default port:** 8080
- **Custom port:** `go run . --port=3000`
- **Build scripts:** `build_and_test_sh.sh`, `build_and_test_ps1.ps1`
- **Bridge:** FFI -- requires the FFI library to be built first

---

## API Endpoints

Each server generates one `POST` endpoint per calculation method defined in your Excel workbook. For example, if your workbook defines a calculation called `monthly_payment`, the server exposes:

```
POST /monthly_payment
Content-Type: application/json

{
  "interest_rate": 5.5,
  "loan_amount": 250000,
  "term_years": 30
}
```

Response:

```json
{
  "monthly_payment": 1419.47
}
```

All servers support CORS, allowing browser-based clients to call the API directly.

### Accept-Language Header

All generated servers accept an optional `Accept-Language` HTTP header. When present, the server applies locale-appropriate number and currency formatting for that request. For example, sending `Accept-Language: de` formats numbers with a comma as the decimal separator.

See [Runtime Formatting](../runtime-formatting.md) for details.

---

## Default Ports

| Server | Default Port |
|--------|-------------|
| Rust | 3030 |
| Java | 7000 |
| Kotlin | 7000 |
| C# | 5000 |
| Go | 8080 |

---

## OpenAPI Documentation

When you generate the OpenAPI Document target, a `open-api.json` file is produced. This is an OpenAPI 3.0.3 specification describing all endpoints, request/response schemas, and server URLs. You can import this into tools like Swagger UI, Postman, or any API documentation tool.

See [Integrations](./integrations.md) for more details.