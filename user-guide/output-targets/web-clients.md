<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Web Clients

Web client libraries are generated code that calls the REST API server. They provide typed methods for each calculation, handling serialization, HTTP requests, and deserialization automatically.

---

## Available Web Clients

### Rust Web Client

- **Build system:** Cargo
- **Library:** reqwest (HTTP client)
- **Build:** `cargo build`
- **Test:** `./build_and_test.sh` or `./build_and_test.ps1`

### Java Web Client

- **Build system:** Gradle
- **Prerequisites:** JDK 11+
- **Build:** `./gradlew build`
- **Test:** `./gradlew test`
- **Configuration:** Set `API_HOST` system property (default: `http://localhost:3030`)

### Kotlin Web Client

- **Build system:** Gradle with Kotlin plugin
- **Prerequisites:** JDK 8+
- **Build:** `./gradlew build`
- **Test:** `./gradlew test`

### C# Web Client

- **Build system:** .NET 8.0
- **Build:** `dotnet build`
- **Test:** `dotnet test`

### Python Web Client

- **Build system:** setuptools
- **Prerequisites:** Python 3.7+
- **Install:** `pip3 install .`
- **Test:** `pytest -s`

### Go Web Client

- **Build system:** Go Modules
- **Prerequisites:** Go 1.21+
- **Build:** `go build ./...`
- **Test:** `go test -v ./test/`

### JavaScript Web Client

- **Build system:** npm
- **Build:** `npm run build`
- **Test:** `npm run test`
- **Output:** Browser-ready JavaScript in `dist/`
- **Configuration:** Update `src/config.js` with your server's base URL

### TypeScript Web Client

- **Build system:** npm with TypeScript 5.8
- **Build:** `npm run build`
- **Test:** `npm run test`
- **Output:** Compiled JavaScript in `dist/`
- **Configuration:** Update `src/config.ts` with your server's base URL

### Swift Web Client

- **Build system:** Swift Package Manager
- **Prerequisites:** Swift 5.5+
- **Build:** `swift build`
- **Test:** `swift test`

---

## Configuration

Each web client includes a configuration file where you set the base URL of the server it should connect to. By default, this points to `http://localhost` on the server's default port.

| Client | Configuration File | Default URL |
|--------|-------------------|-------------|
| JavaScript | `src/config.js` | `http://localhost:3030` |
| TypeScript | `src/config.ts` | `http://localhost:3030` |
| Java | System property `API_HOST` | `http://localhost:3030` |
| Others | Source constant | `http://localhost:3030` |

Update this to match your deployment environment before building for production.