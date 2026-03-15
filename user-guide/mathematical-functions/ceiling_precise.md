<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## CEILING.PRECISE Function

The `CEILING.PRECISE` function in Excel rounds a number up to the nearest multiple of a specified factor. It's designed to provide consistent rounding behavior across positive and negative numbers, effectively making rounding more predictable than older functions.

### Syntax:

    CEILING.PRECISE(number, [significance])\


- **number**: The value you want to round.
- **significance** (optional): The multiple to which you want to round. If omitted, the default is 1.

### Examples:

1. `=CEILING.PRECISE(4.1, 0.5)` would return `4.5` because 4.1 rounded up to the nearest 0.5 is 4.5.
2. `=CEILING.PRECISE(-4.1, 0.5)` would return `-4.0`. With `CEILING.PRECISE`, negative numbers are always rounded up (toward zero).

> **Note**: The main difference between `CEILING.PRECISE` and the traditional `CEILING` function is the consistent rounding behavior for negative numbers. `CEILING.PRECISE` will always round away from zero, regardless of whether the number is positive or negative.