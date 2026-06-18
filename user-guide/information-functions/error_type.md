<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ERROR.TYPE Function

The `ERROR.TYPE` function in Excel returns a **numeric code identifying which specific error a value represents**. Where `ISERROR` only tells you *whether* there is an error, `ERROR.TYPE` tells you *which* one — making it possible to display custom messages or take different actions depending on the kind of failure. It is most commonly paired with `IF` and `CHOOSE` to map each error code to a tailored response.

## Key Features of `ERROR.TYPE`:

- Returns `1` for `#NULL!`, `2` for `#DIV/0!`, `3` for `#VALUE!`, `4` for `#REF!`, `5` for `#NAME?`, `6` for `#NUM!`, and `7` for `#N/A`.
- Returns the `#N/A` error itself when the input is **not** an error (so the result of `ERROR.TYPE` on a number, text, or logical is `#N/A`).
- Works seamlessly with `CHOOSE` to map each code to a human-readable message.
- Lets you distinguish a "value not available" (`#N/A`) from a "calculation broke" (`#DIV/0!`, `#VALUE!`, etc.) and respond accordingly.
- Complements `ISERROR` (presence) and `TYPE` (data category — returns 16 for any error, without distinguishing which).

## Syntax:

```plaintext
ERROR.TYPE(error_val)
```

- **error_val**: The value or expression whose error type you want to identify. Typically a cell reference or the result of a formula that may produce an error.

## How `ERROR.TYPE` Works:

1. `ERROR.TYPE` inspects the supplied value.
2. If it is one of the seven Excel error values, it returns the corresponding numeric code:

    | Error      | Code |
    | ---------- | ---- |
    | `#NULL!`   | 1    |
    | `#DIV/0!`  | 2    |
    | `#VALUE!`  | 3    |
    | `#REF!`    | 4    |
    | `#NAME?`   | 5    |
    | `#NUM!`    | 6    |
    | `#N/A`     | 7    |

3. If the input is not an error (a number, text, logical, blank, etc.), `ERROR.TYPE` returns `#N/A`.
4. Because the result is itself a number or `#N/A`, `ERROR.TYPE` is almost always wrapped in `IF(ISERROR(x), …, x)` so that it is only invoked on confirmed errors.

## Examples:

### 1. Identify a #N/A Error:

```excel
=ERROR.TYPE(NA())
```

**Result:**
```
7
```

### 2. Identify a #DIV/0! Error:

If A1 contains `=1/0`:
```excel
=ERROR.TYPE(A1)
```

**Result:**
```
2
```

### 3. Non-Error Input Returns #N/A:

If A1 contains `100`:
```excel
=ERROR.TYPE(A1)
```

**Result:**
```
#N/A
```

### 4. Custom Message Per Error Type:

```excel
=IF(ISERROR(A1), CHOOSE(ERROR.TYPE(A1),
    "Empty intersection",
    "Cannot divide by zero",
    "Wrong type",
    "Invalid reference",
    "Unknown name",
    "Invalid number",
    "Not available"), A1)
```

**Result:**
```
Returns the value in A1 if it's not an error, otherwise a tailored message for the specific error.
```

### 5. Lookup with Error-Specific Fallback:

```excel
=IF(ISERROR(VLOOKUP(A1, D:E, 2, FALSE)),
    IF(ERROR.TYPE(VLOOKUP(A1, D:E, 2, FALSE))=7, "Not in catalog", "Lookup failed"),
    VLOOKUP(A1, D:E, 2, FALSE))
```

**Result:**
```
Distinguishes a missing key (#N/A → "Not in catalog") from a malformed lookup (other errors → "Lookup failed").
```

### 6. Logging Which Error Occurred:

```excel
=IF(ISERROR(A1), "Error code " & ERROR.TYPE(A1), "OK")
```

**Result:**
```
"Error code 2" when A1 is #DIV/0!, "Error code 7" when A1 is #N/A, "OK" when A1 has a valid value.
```

### 7. Branching on Recoverable vs. Fatal Errors:

```excel
=IF(ISERROR(A1), IF(OR(ERROR.TYPE(A1)=2, ERROR.TYPE(A1)=6), 0, "Check formula"), A1)
```

**Result:**
```
Treats #DIV/0! and #NUM! as "0" (recoverable) and any other error as needing review.
```

### 8. Counting Errors by Type in a Range:

```excel
=SUMPRODUCT((ISERROR(A1:A10)) * (IFERROR(ERROR.TYPE(A1:A10), 0) = 2))
```

**Result:**
```
Counts how many cells in A1:A10 contain #DIV/0! specifically.
```

## Notes:

- `ERROR.TYPE` always returns `#N/A` for non-error inputs — so calling it without an `ISERROR` guard yields `#N/A`, which is rarely what you want.
- In current Excel, codes 1–7 are stable across versions. Some versions also expose code 8 for `#GETTING_DATA`, which Codcel does not currently emit.
- `ERROR.TYPE` is the only Excel function that lets you programmatically distinguish between the seven error tokens — `ISERROR`/`ISERR`/`ISNA` only return TRUE/FALSE for membership in particular sets of errors.
- When operating on an array or range, `ERROR.TYPE` returns an array of codes (or `#N/A` for non-error cells), which pairs well with `SUMPRODUCT` for category counting.
- In Codcel, errors that propagate through arithmetic without a specific type attached are reported as `7` (`#N/A`) — the same code Excel uses as the fallback for unidentified errors. Errors produced by database functions (`DGET`, `DSTDEV`, etc.) are reported with their original type.

## Applications:

- **User-Friendly Error Messages**: Show a tailored explanation per error type instead of a raw `#VALUE!` or `#REF!` token.
- **Error Triage**: Separate "data not found" (`#N/A`) from "formula broken" (`#REF!`, `#VALUE!`) so each can be routed to a different handler.
- **Audit & Reporting**: Categorize and count errors in a dataset by type for quality dashboards.
- **Conditional Recovery**: Treat some errors as recoverable (substitute a default) and others as fatal (require manual review).
- **Diagnostic Logging**: Record the specific error code alongside a formula's result for downstream analysis.

## Related Functions:

- **[ISERROR](./iserror.md)**: Returns TRUE if the value is any error — the usual guard before calling `ERROR.TYPE`.
- **[ISERR](./iserr.md)**: Returns TRUE for any error *except* `#N/A`.
- **[ISNA](./isna.md)**: Returns TRUE only for `#N/A` — narrower than `ERROR.TYPE` if you only care about lookup failures.
- **[NA](./na.md)**: Returns the `#N/A` error explicitly — useful when you want to flag missing data deliberately.
- **[IFERROR](../conditional-functions/if_error.md)**: Returns a fallback value if a formula evaluates to any error.
- **[IFNA](../logical-functions/ifna.md)**: Returns a fallback value if a formula evaluates to `#N/A` specifically.
- **[TYPE](./type.md)**: Returns a numeric code for the broad data type of a value (16 for any error, without distinguishing which).

> **Tip:** Always wrap `ERROR.TYPE` in an `IF(ISERROR(...), CHOOSE(ERROR.TYPE(...), …), …)` pattern so it never runs on a non-error input. The `CHOOSE` trick — passing the code into a list of seven strings — is the canonical idiom for mapping each error type to a custom message in a single, readable formula.
