<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PRODUCT Function

The `PRODUCT` function in Excel multiplies all the numbers given as arguments and returns the product. This function is particularly useful for multiplying several numbers together without having to use the asterisk (`*`) repeatedly.

### Syntax:

    PRODUCT(number1, [number2], ...)


- **number1**: The first number you want to multiply.
- **number2, ...** (optional): Additional numbers you want to multiply with `number1`. You can specify up to 255 numbers in total.

### Examples:

1. `=PRODUCT(2, 3, 4)` would return `24`, as it multiplies 2 by 3 by 4.
2. `=PRODUCT(A1:A5)` would multiply all the numbers in the range `A1:A5`.
3. `=PRODUCT(1.5, A1, B2, 10)` would multiply 1.5, the value in cell A1, the value in cell B2, and 10 together.

### Usage Notes:
- If any of the arguments are non-numeric, `PRODUCT` will ignore them.
- An empty cell in a range is treated as 1 (since multiplying by 1 has no effect on the product).
- If you want to include only specific types of values (like positive numbers) or need to apply conditions, you might have to use additional functions in conjunction with `PRODUCT`.

> **Note**: `PRODUCT` is a fundamental arithmetic function and is especially useful in financial and scientific calculations where you need to multiply a series of factors.