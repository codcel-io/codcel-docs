<!--
SPDX-FileCopyrightText: Copyright (c) 2026 Codcel
SPDX-License-Identifier: CC-BY-4.0

This file is part of the Codcel documentation (https://codcel.io).
See LICENSE in the project root.
-->

## MIN Function

The `MIN` function in Excel returns the smallest number in a set of values. It ignores logical values, empty cells, and text.

### Syntax:

    MIN(number1, [number2], ...)

- **number1**: The first number or range from which you want to find the smallest number.
- **number2, ...** (optional): Additional numbers or ranges.

### Examples:

1. `=MIN(3, 5, 1, 8)` would return `1`, since 1 is the smallest number in the set.
2. If cells A1:A5 contain the values `10, 15, 5, 20, 25`, the formula `=MIN(A1:A5)` would return `5`.

> **Note**: While `MIN` is primarily used for numeric values, it can be used in a range that includes text values. In such cases, text and logical values are ignored.

> **Note**: Currently Codcel only supports MIN for numerical values.