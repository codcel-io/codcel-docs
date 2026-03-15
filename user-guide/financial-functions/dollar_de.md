<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DOLLARDE Function

The `DOLLARDE` function in Excel converts a **price expressed as a fraction** into its equivalent **decimal value**. It
is commonly used in financial analysis, especially in scenarios involving prices of securities expressed in fractional
format (e.g., stock quotes).

## Key Features of DOLLARDE:

- Converts fractional notation (commonly used in finance) into decimal notation.
- Useful for working with prices where the fractional part doesn't correspond to standard decimal values (e.g.,
  quarters, eighths, or sixteenths).

## Syntax:

```plaintext
DOLLARDE(fractional_number, fraction)
```

### Arguments:

- **fractional_number**: The number to convert from fractional to decimal format.
    - The integer part represents the whole number portion.
    - The fractional part represents the numerator of the fraction based on the given **fraction**.
- **fraction**: The denominator used for the fraction. It must be greater than 0.

## How It Works:

1. The function interprets the **fractional_number** based on the given **fraction** to calculate the decimal value.
2. For example, a fractional stock price of `1.08` (with a denominator 8) is interpreted as:
    - Whole part: `1`
    - Fractional: `8 ÷ 8 = 1`
    - Result: `1.0 + (8/8) = 1.125`.

## Examples:

### 1. Converting Fractional to Decimal:

```excel
=DOLLARDE(1.08, 8)
```

**Result:** `1.125`

This converts the fractional value `1.08` (1 and 8/8) into its decimal equivalent, `1.125`.

---

### 2. Using Sixteenths for Conversion:

```excel
=DOLLARDE(3.04, 16)
```

**Result:** `3.25`

This converts the fractional value `3.04` (3 and 4/16) into its decimal equivalent, `3.25`.

---

### 3. Handling a Custom Denominator:

```excel
=DOLLARDE(10.03, 12)
```

**Result:** `10.25`

This converts the fractional value `10.03` (10 and 3/12) into its decimal equivalent, `10.25`.

## Notes:

- If **fraction** is less than or equal to 0, the function returns a `#NUM!` error.
- If the **fractional_number** contains invalid characters or is improperly formatted, the function returns a `#VALUE!`
  error.
- In financial contexts, ensure that the denominator of the fraction matches the base of the fractional notation (e.g.,
  8 for eighths, 16 for sixteenths).

## Applications:

- **Stock Price Conversions**: Often used by financial analysts to interpret and process stock prices quoted in
  fractional notations.
- **Bond Markets**: Useful for converting quoted bond prices from fractional to decimal formats.
- **Investment Calculations**: Simplifies computations requiring decimal values instead of fractions.

> **Tip:** Use `DOLLARDE` in conjunction with `DOLLARFR` if you need to toggle between fractional and decimal formats in
> financial calculations. For example, fractional prices can be decoded into decimals for easier arithmetic operations.