<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Functional Programming in Excel

Excel 365 introduced several functions that bring functional programming concepts to spreadsheets. Codcel supports all of these functions and transpiles them into equivalent constructs in the generated code.

---

## Overview

Functional programming in Excel centres on the LAMBDA function, which lets you define anonymous functions, and a set of higher-order functions that apply lambdas across arrays.

---

## Core Functions

### LAMBDA

Defines an anonymous function with named parameters.

```excel
=LAMBDA(x, y, x + y)
```

Codcel fully supports LAMBDA expressions, both inline and named (defined in the Name Manager). See [LAMBDA Support](./differences/lambda-support.md) for details.

### LET

Assigns names to intermediate values within a formula, improving readability and avoiding repeated calculation.

```excel
=LET(tax, 0.2, price, 100, price * (1 + tax))
```

---

## Higher-Order Functions

These functions take a LAMBDA as an argument and apply it across data:

| Function | Description | Example |
|----------|-------------|---------|
| [MAP](./logical-functions/map.md) | Apply a function to each element | `=MAP(A1:A10, LAMBDA(x, x * 2))` |
| [REDUCE](./logical-functions/reduce.md) | Accumulate values using a function | `=REDUCE(0, A1:A5, LAMBDA(acc, x, acc + x))` |
| [SCAN](./logical-functions/scan.md) | Like REDUCE but returns intermediate results | `=SCAN(0, A1:A5, LAMBDA(acc, x, acc + x))` |
| [BYROW](./logical-functions/byrow.md) | Apply a function to each row of an array | `=BYROW(A1:C5, LAMBDA(row, SUM(row)))` |
| [BYCOL](./logical-functions/bycol.md) | Apply a function to each column of an array | `=BYCOL(A1:C5, LAMBDA(col, AVERAGE(col)))` |
| [MAKEARRAY](./logical-functions/makearray.md) | Generate an array using a function | `=MAKEARRAY(3, 3, LAMBDA(r, c, r * c))` |

---

## Data Grouping

### GROUPBY

Groups data by a key column and applies an aggregation function to each group.

```excel
=GROUPBY(A2:A20, B2:B20, LAMBDA(values, AVERAGE(values)))
```

This is similar to SQL's `GROUP BY` clause and is useful for summarising datasets.

---

## How Codcel Transpiles These

In the generated code, these functional constructs are translated into the target language's equivalent:

- **Rust:** Closures and iterators (`.map()`, `.fold()`, etc.)
- **Java/Kotlin:** Lambda expressions and streams
- **Python:** Lambda functions and list comprehensions
- **C#:** LINQ expressions and lambda delegates
- **Go:** Function values and loops

The generated code is idiomatic for each language while preserving the calculation logic.

---

## See Also

- [LAMBDA Support](./differences/lambda-support.md) -- named LAMBDA support details
- [Logical Functions](./logical-functions.md) -- function reference including MAP, REDUCE, SCAN
- [Dynamic Arrays](./dynamic-arrays.md) -- array-producing functions