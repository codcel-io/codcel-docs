<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ISO.CEILING Function

The `ISO.CEILING` function in Excel is used to round up a number to the nearest integer or specified multiple, moving
away from zero. This function is useful in scenarios requiring standardized rounding up, such as financial calculations
or inventory adjustments.

### Syntax:

    ISO.CEILING(number, [significance])

- **number**: The numeric value you want to round.
- **significance** *(optional)*: The multiple to which you want to round the number. Defaults to `1` if omitted.

### Examples:

1. `=ISO.CEILING(4.3)`  
   Returns `5`, as the number `4.3` is rounded up to the nearest integer.

2. `=ISO.CEILING(4.3, 0.5)`  
   Returns `4.5`, as `4.3` is rounded up to the next multiple of `0.5`.

3. `=ISO.CEILING(-4.3)`  
   Returns `-5`, because the negative number `-4.3` rounds away from zero.

4. `=ISO.CEILING(-4.3, 0.5)`  
   Returns `-4.5`, rounding to the next multiple of `0.5` away from zero.

5. `=ISO.CEILING(12.7, 5)`  
   Returns `15`, as `12.7` is rounded up to the next multiple of `5`.

### Usage Notes:

- The **significance** value must be positive; if omitted, it defaults to `1`.
- For positive numbers, the function behaves similarly to `CEILING` but ensures a consistent, ISO-compliant rounding
  behavior.
- For negative numbers, the function rounds away from zero, unlike `CEILING` with some combinations of arguments.
- `ISO.CEILING` is particularly useful in industries requiring precise and standardized rounding, such as finance,
  manufacturing, or logistics.