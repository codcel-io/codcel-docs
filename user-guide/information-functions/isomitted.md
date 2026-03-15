<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ISOMITTED Function

The `ISOMITTED` function in Excel is used to **check whether an argument was omitted** in a LAMBDA function. It returns TRUE if the argument was not provided when the LAMBDA was called, and FALSE if a value was supplied. This function is essential for creating LAMBDA functions with optional parameters and default value handling.

## Key Features of `ISOMITTED`:

- Detects whether an optional argument was omitted in a LAMBDA call.
- Returns `TRUE` if the argument was omitted, `FALSE` if it was provided.
- Works exclusively within LAMBDA functions.
- Enables creation of flexible functions with optional parameters.
- Allows implementation of default values for missing arguments.

## Syntax:

```plaintext
ISOMITTED(argument)
```

- **argument**: The LAMBDA parameter you want to check for omission.

## How `ISOMITTED` Works:

1. When called inside a LAMBDA function, `ISOMITTED` checks if the specified parameter was provided.
2. If the argument was omitted (not passed) when calling the LAMBDA, it returns `TRUE`.
3. If any value was provided (including empty string, zero, or FALSE), it returns `FALSE`.
4. This is typically used with `IF` to provide default values for optional parameters.
5. `ISOMITTED` only works within the context of a LAMBDA function.

## Examples:

### 1. Basic LAMBDA with Optional Parameter:

```excel
=LAMBDA(required, optional,
    IF(ISOMITTED(optional), "No optional value", optional)
)("Hello")
```

**Result:**
```
No optional value
```

### 2. Default Value for Omitted Argument:

```excel
=LAMBDA(value, multiplier,
    value * IF(ISOMITTED(multiplier), 2, multiplier)
)(10)
```

**Result:**
```
20
```

(Uses default multiplier of 2 since second argument was omitted)

### 3. With Named LAMBDA Function:

Define a named function `GREET` with optional greeting:
```excel
=LAMBDA(name, greeting,
    IF(ISOMITTED(greeting), "Hello", greeting) & ", " & name & "!"
)
```

Usage:
```excel
=GREET("Alice")
=GREET("Bob", "Hi")
```

**Results:**
```
Hello, Alice!
Hi, Bob!
```

### 4. Multiple Optional Parameters:

```excel
=LAMBDA(base, rate, years,
    base *
    (1 + IF(ISOMITTED(rate), 0.05, rate)) ^
    IF(ISOMITTED(years), 1, years)
)(1000)
```

**Result:**
```
1050
```

(Uses default rate of 5% and 1 year)

### 5. Distinguish Omitted from Empty:

```excel
=LAMBDA(value,
    IF(ISOMITTED(value), "Omitted",
        IF(value="", "Empty string", value))
)
```

Calling with no argument returns "Omitted"
Calling with "" returns "Empty string"
Calling with "test" returns "test"

### 6. Conditional Logic Based on Omission:

```excel
=LAMBDA(data, ascending,
    SORT(data, 1, IF(ISOMITTED(ascending), 1, IF(ascending, 1, -1)))
)
```

**Result:**
```
Sorts ascending by default, or by the specified direction
```

### 7. Recursive LAMBDA with Optional Counter:

```excel
=LAMBDA(n, counter,
    LET(
        c, IF(ISOMITTED(counter), 0, counter),
        IF(n <= 1, c + 1, SELF(n - 1, c + 1))
    )
)
```

**Result:**
```
Counts recursively, starting from 0 if counter is omitted
```

### 8. Complex Function with Multiple Defaults:

```excel
=LAMBDA(amount, tax_rate, discount, currency,
    LET(
        rate, IF(ISOMITTED(tax_rate), 0.1, tax_rate),
        disc, IF(ISOMITTED(discount), 0, discount),
        curr, IF(ISOMITTED(currency), "$", currency),
        total, (amount * (1 + rate)) - disc,
        curr & TEXT(total, "#,##0.00")
    )
)(100)
```

**Result:**
```
$110.00
```

(Uses default 10% tax, no discount, and $ currency)

## Notes:

- `ISOMITTED` only works inside LAMBDA functions; using it elsewhere returns an error.
- An empty string `""` passed as an argument is NOT considered omitted — `ISOMITTED` returns `FALSE`.
- Zero, FALSE, and other "falsy" values are NOT considered omitted.
- `ISOMITTED` is the only reliable way to detect truly omitted arguments in LAMBDA.
- This function is crucial for building robust, flexible custom functions.

## Applications:

- **Default Parameters**: Provide sensible defaults when users don't specify all arguments.
- **Flexible Functions**: Create functions that adapt behavior based on which arguments are provided.
- **Backward Compatibility**: Add new optional parameters to existing LAMBDA functions without breaking existing usage.
- **Overloaded Behavior**: Implement different logic paths depending on the number of arguments provided.
- **User-Friendly Functions**: Allow users to call functions with minimal required inputs.

## Related Functions:

- **LAMBDA**: Creates custom, reusable functions that can have optional parameters.
- **LET**: Assigns names to calculation results, often used with LAMBDA for complex logic.
- **IF**: Used with ISOMITTED to provide conditional default values.
- **IFERROR**: Handles errors in function execution.
- **ISBLANK**: Tests whether a cell is empty (different from checking if an argument is omitted).

> **Tip:** When designing LAMBDA functions with optional parameters, always place required parameters first and optional parameters last. Use `ISOMITTED` with `IF` to provide meaningful defaults, and document your default values so users know what to expect when they omit arguments.