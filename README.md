<p align="center">
  <a href="https://codcel.io">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/codcel-logo-lockup-dark.svg">
      <img src="assets/codcel-logo-lockup.svg" alt="Codcel" width="320">
    </picture>
  </a>
</p>

# Codcel Documentation

Open-source documentation for [Codcel](https://codcel.io) — written in Markdown, version-controlled, and community-improvable.

## Overview

This repository contains the official documentation for Codcel, a platform that converts Excel spreadsheets into production-ready source code in Rust, Python, Java, C#, TypeScript, Go, Swift, and more. Everything here is open — read it, suggest improvements, and contribute alongside us.

## User Guide

**[Read the full User Guide →](user-guide/index.md)**

The user guide covers everything from getting started to architecture:

- **Getting Started** — introduction, desktop app, Excel-to-code workflow, annotations, settings, CLI, testing
- **Output Targets** — calculation libraries, REST servers, web clients, fullstack UI, integrations (OpenAPI, CLI, MCP, JNI, FFI)
- **Tables & Data** — tables, CRUD operations, named ranges
- **Excel Concepts** — dynamic arrays, functional programming, circular references
- **Excel Function References** — 460+ supported functions across 13 categories (financial, statistical, mathematical, engineering, text, date/time, lookup, logical, and more)
- **Performance & Large Data** — big data handling, One Billion Row Challenge
- **Differences** — where Codcel differs from Excel (rounding, date handling, type conversions)
- **Troubleshooting** — error and warning codes
- **Architecture** — how Codcel works under the hood

## Open-Source Engines

Codcel's core engines are open source. The generated projects you get from Codcel call into these libraries directly — no black boxes.

| Engine | Description |
|---|---|
| [Codcel Calculation Engine](https://github.com/codcel-io/codcel-calculation-engine) | 460+ Excel-compatible functions implemented in pure Rust |
| [Codcel Table Engine](https://github.com/codcel-io/codcel-table-engine) | Shared traits and utilities for Excel-like table operations |
| [Codcel Parquet Engine](https://github.com/codcel-io/codcel-parquet-engine) | Read-only Parquet table engine with query caching |
| [Codcel PostgreSQL Engine](https://github.com/codcel-io/codcel-postgresql-engine) | Full CRUD PostgreSQL table engine with connection pooling |

## Contributing

Contributions are welcome! Whether it's fixing a typo, improving an example, or documenting missing behavior — please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

## About Codcel

[Codcel](https://codcel.io) turns Excel spreadsheets into production-ready software — real source code in Rust, Python, Java, C#, TypeScript, Go, Swift, and more, with zero platform lock-in.

This documentation is one of several open-source components that power Codcel. Learn more at [codcel.io](https://codcel.io).

## Licensing

This documentation is dual-licensed:

- **[Creative Commons Attribution 4.0 (CC BY 4.0)](LICENSE-CC-BY)** — for general use
- **[Codcel Documentation License](LICENSE-CODCEL-DOCS)** — applies if this documentation is used as part of an Automated Code Generation System or competing spreadsheet-to-code platform

See [LICENSING.md](LICENSING.md) for details.
