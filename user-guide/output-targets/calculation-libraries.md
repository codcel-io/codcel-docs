<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Calculation Libraries

Calculation libraries are standalone libraries that you embed in your own applications. They contain the transpiled Excel calculations as native functions in your chosen language.

All non-Rust calculation libraries wrap the Rust engine via JNI (Java/Kotlin) or FFI (C#, Visual Basic, Python, Go, Swift), combining the performance of native Rust with the convenience of your preferred language.

---

## Rust Calculation Library

The core engine. Always generated and required by all other targets.

- **Build system:** Cargo
- **Build:** `cargo build --release`
- **Test:** `cargo test`

---

## WASM Calculation Library

A WebAssembly version of the calculation engine for use in web browsers.

- **Build system:** Cargo (with `wasm-pack`)
- **Prerequisites:** [wasm-pack](https://rustwasm.github.io/wasm-pack/installer/)
- **Build:** `wasm-pack build --target web`
- **Output:** JavaScript/TypeScript bindings in `pkg/`
- **Use case:** Run calculations directly in the browser without a server

---

## Java Calculation Library

- **Build system:** Gradle
- **Prerequisites:** JDK 11+
- **Build:** `./gradlew build`
- **Test:** `./gradlew test`
- **Dependencies:** Jackson (JSON), JUnit 5
- **Bridge:** JNI -- requires the JNI library to be built first (`cargo build --release` in the `jni/` directory)

The generated library includes Input, Output, and Calculation classes. The Calculation class delegates to Rust via JNI for performance.

---

## Kotlin Calculation Library

- **Build system:** Gradle with Kotlin plugin
- **Prerequisites:** JDK 8+, Kotlin 2.0+
- **Build:** `./gradlew build`
- **Test:** `./gradlew test`
- **Dependencies:** Kotlinx Serialization, JUnit 5
- **Bridge:** JNI -- requires the JNI library to be built first

---

## C# Calculation Library

- **Build system:** .NET 8.0
- **Prerequisites:** .NET 8 SDK
- **Build:** `dotnet build -p:CodcelTargetOS=<os>`
- **Test:** `dotnet test -p:CodcelTargetOS=<os>`
- **OS parameter:** `linux`, `macos`, or `windows`
- **Bridge:** FFI -- requires the FFI library to be built first (`cargo build --release` in the `ffi/` directory)
- **Build scripts:** `build_and_test_sh.sh` (Linux/Mac), `build_and_test_ps1.ps1` (Windows)

---

## Visual Basic Calculation Library

- **Build system:** .NET 8.0
- **Prerequisites:** .NET 8 SDK
- **Build:** `dotnet build -p:CodcelTargetOS=<os>`
- **Test:** `dotnet test -p:CodcelTargetOS=<os>`
- **OS parameter:** `linux`, `macos`, or `windows`
- **Bridge:** FFI -- requires the FFI library to be built first

---

## Python Calculation Library

- **Build system:** setuptools
- **Prerequisites:** Python 3.7+
- **Install:** `pip3 install .`
- **Test:** `pytest -s`
- **Dependencies:** pydantic, pytest
- **Bridge:** FFI -- requires the FFI library to be built first

---

## Go Calculation Library

- **Build system:** Go Modules
- **Prerequisites:** Go 1.21+; TDM-GCC on Windows (for CGO)
- **Build:** `go mod tidy && go build ./...`
- **Test:** `go test -v ./test/`
- **Dependencies:** testify
- **Bridge:** FFI -- requires the FFI library to be built first
- **Environment:** `CODCEL_TABLE_PATH` must be set if the project uses tables

---

## Swift Calculation Library

- **Build system:** Swift Package Manager
- **Prerequisites:** Swift 5.5+; macOS 10.15+ or Linux
- **Build:** `swift build`
- **Test:** `swift test`
- **Bridge:** FFI -- requires the FFI library to be built first
- **Environment:** `CODCEL_TABLE_PATH` must be set if the project uses tables

---

## Per-Call Language Override

Every generated calculation library provides a `_with_language` (or `WithLanguage`) variant that accepts a language tag string (e.g. `"de"`, `"fr-FR"`). This applies locale-appropriate formatting for that single calculation call without changing the default formatting for other calls.

See [Runtime Formatting](../runtime-formatting.md#per-call-language-override-calculation-libraries) for code examples in each language.

---

## Build Order

For any non-Rust calculation library:

1. Build the Rust Calculation Library: `cargo build --release`
2. Build the bridge library:
   - For Java/Kotlin: `cargo build --release` in the `jni/` directory
   - For C#/VB/Python/Go/Swift: `cargo build --release` in the `ffi/` directory
3. Build the target-language library using its build system