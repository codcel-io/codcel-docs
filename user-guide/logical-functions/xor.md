<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->


# Excel XOR Function

The `XOR` function in Excel is a logical function that returns a logical Exclusive OR of all the arguments provided. It evaluates whether an odd number of the provided conditions are TRUE. If an odd number of conditions evaluate to TRUE, the function returns `TRUE`. Otherwise, it returns `FALSE`.

## Syntax
```
XOR(logical1, [logical2], ...)
```

- `logical1` (required): The first condition to evaluate.
- `[logical2], ...` (optional): Additional conditions to evaluate. Up to 254 logical arguments can be included.

## Key Characteristics
1. **Exclusive OR**: 
   - If only one condition is TRUE, the result is `TRUE`.
   - If an even number of conditions are TRUE (including none), the result is `FALSE`.

2. **Behavior with Errors**:
   - If any argument contains an error, the function will return that error.

3. **Flexible Input**:
   - Arguments can be logical values, arrays, or references containing logical values.

## Example Usage
### Example 1: Basic Usage
| Formula                      | Result |
|------------------------------|--------|
| `=XOR(TRUE, FALSE)`          | TRUE   |
| `=XOR(TRUE, TRUE)`           | FALSE  |
| `=XOR(FALSE, FALSE)`         | FALSE  |

### Example 2: Using Cell References
If:
- Cell A1 contains `TRUE`
- Cell A2 contains `FALSE`
- Cell A3 contains `TRUE`

Then:
```
=XOR(A1, A2, A3)
```
Result: `TRUE` (Since there is an odd number of TRUE values).

## Applications
- Used in conditional calculations where exclusive conditions are needed.
- Helpful in creating complex logical tests for filtering or decision-making.

## Notes
- The `XOR` function was introduced in Excel 2013 and is available in later versions.