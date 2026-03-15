<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Testing and Validation

Codcel automatically generates test documentation that compares the output of the generated code against the values in your Excel workbook. This is your first line of defence for verifying that the transpiled calculations match your spreadsheet.

---

## What Gets Generated

For each output cell annotated with `*O*`, Codcel generates a test case that:

1. Sets up the input values as they appear in the Excel workbook
2. Runs the generated calculation function
3. Compares the result to the expected value from Excel

The tests are generated in the native test framework for each output target.

---

## Running Tests by Target

### Rust

```bash
cargo test
```

Tests are in the standard Rust `#[test]` format and run with `cargo test`.

### Java

```bash
./gradlew test
```

Tests use JUnit 5. Test results appear in `build/reports/tests/`.

### Kotlin

```bash
./gradlew test
```

Tests use JUnit 5 with Kotlin syntax.

### C# / Visual Basic

```bash
dotnet test -p:CodcelTargetOS=<os>
```

Replace `<os>` with `linux`, `macos`, or `windows`. Tests use the .NET test framework.

### Python

```bash
pytest -s
```

Tests use pytest.

### Go

```bash
go test -v ./test/
```

Tests use the standard Go testing package with testify assertions.

### Swift

```bash
swift test
```

Tests use Swift's XCTest framework.

---

## Interpreting Test Results

Each test compares an expected value (from Excel) against an actual value (from the generated code).

- **Pass:** The generated code produces the same result as Excel
- **Fail:** There is a difference between Codcel's output and Excel's value

A failing test does not necessarily mean the generated code is wrong. Possible reasons for differences include:

- **Rounding:** Floating-point precision differences (see [Rounding](./differences/rounding.md))
- **Type conversion:** Different implicit conversion behaviour (see [Type Conversions](./differences/type-conversions.md))
- **Function-specific differences:** Some functions have known precision variations (see [Known Function Differences](./differences/known-function-differences.md))
- **Non-deterministic functions:** Functions like RAND, RANDBETWEEN, and RANDARRAY produce different values on every run, so tests using these will always fail. To avoid this, replace random values with static values in your workbook before importing (copy and paste as values).

---

## Limitations

The generated tests verify calculations using the **single set of input values** present in your Excel workbook at the time of import. They do not test:

- Different input combinations
- Edge cases (empty values, very large numbers, boundary conditions)
- Error handling paths

For production use, you should supplement the generated tests with your own test cases covering the input ranges relevant to your application.

---

## Testing with the Fullstack UI

The generated [Fullstack UI](./output-targets/fullstack-ui.md) includes built-in testing tools accessible from the **Tests** button in the top right of the application. Everything runs locally — no data leaves your machine.

### Run Tests

Upload a CSV file containing input values and optional expected outputs. Codcel runs the calculation for each row and reports pass or fail.

- Expected output columns are marked with `*T*` (e.g. `*T*cost`) — these are the values Codcel checks against
- If no expected outputs are included, Codcel simply runs the calculation and verifies it completes without errors
- After running, you can download the results as a CSV with the calculated outputs filled in — this gives you a verified test file you can re-use

### Create Tests

Instead of writing test cases by hand, define a range for each input:

- **Min** — lowest value to test
- **Max** — highest value to test
- **Step** — increment between values

Codcel generates all input combinations automatically. For example, a price ranging from £1 to £5 in £0.10 steps combined with a tip from £0 to £3 in £0.50 steps produces hundreds of test cases.

The generated CSV contains inputs only. Run it through **Run Tests** to execute the calculations, then download the results to get a complete test file with expected outputs.

### Typical Workflow

1. Use **Create Tests** to generate input combinations covering your expected ranges
2. Run the generated CSV through **Run Tests** to verify all calculations succeed
3. Download the results CSV — it now contains both inputs and expected outputs
4. Re-upload this file at any time to verify that calculations still produce the same results

This is your responsibility — Codcel provides the tools, but validating that results are correct for your use case is up to you.

---

## Adding Custom Tests

The generated test files follow standard testing conventions for each language. You can add additional test cases to these files or create new test files alongside them using the same testing framework.

---

## See Also

- [Differences from Excel](./differences.md) -- understanding where results may differ
- [Excel to Code](./excel-to-code.md) -- the complete workflow including testing
- [Output Targets](./output-targets.md) -- build and test commands for each target