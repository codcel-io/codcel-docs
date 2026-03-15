<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# LAMBDA Support

Codcel fully supports the LAMBDA function, including all higher-order functions that use lambdas (MAP, REDUCE, SCAN, BYROW, BYCOL, MAKEARRAY) and named LAMBDAs defined in Excel's Name Manager.

---

## Inline LAMBDAs

Inline LAMBDA expressions work directly in formulas:

```excel
=MAP(A1:A10, LAMBDA(price, price * 1.2))
```

---

## Named LAMBDAs

You can define a LAMBDA as a named range in the Name Manager and call it by name like a custom function. Codcel reads these definitions from the workbook and generates a shared function for each named LAMBDA.

**Example:**

1. Define a named range `AddTax` with formula `=LAMBDA(price, price * 1.2)`
2. Use `=AddTax(100)` in a cell

Codcel generates a single reusable function for `AddTax` and all call sites share it.

---

## Recursive Named LAMBDAs

Self-recursive named LAMBDAs are also supported. For example, you can define `FACTORIAL` in the Name Manager:

```
=LAMBDA(n, IF(n <= 1, 1, n * FACTORIAL(n - 1)))
```

Then use `=FACTORIAL(5)` in a cell to get `120`.

Codcel detects the recursion and generates the appropriate code to handle it correctly in each target language.