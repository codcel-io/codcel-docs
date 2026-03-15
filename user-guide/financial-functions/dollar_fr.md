<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DOLLARFR Function

The `DOLLARFR` function in Excel converts a **decimal number** into its equivalent **fractional value**, based on a
specified denominator. This function is commonly used in financial settings where prices are expressed in fractional
notation, such as in stock markets or bond pricing.

## Key Features of DOLLARFR:

- Converts a decimal value into fractional notation based on a provided denominator.
- Useful for working with prices quoted in fractions (e.g., 1/8, 1/16, or 1/32).
- Complements the `DOLLARDE` function, which performs the reverse operation.

## Syntax:

```plaintext
DOLLARFR(decimal_number, fraction)
```

### Arguments:

- **decimal_number**: The decimal number you want to convert to fractional format.
    - The integer part represents the whole part of the number.
    - The fractional part is converted into the given fraction's denominator.
- **fraction**: The denominator used to convert the fractional part of the **decimal_number**. This must be greater than
  0.

## How It Works:

1. The function interprets the **decimal_number** to create a fractional price using the whole number part and the
   fractional denominator.
2. For example, a decimal value of `1.125` (with a denominator of 8) is transformed into:
    - Whole part: `1`
    - Fractional Conversion: `0.125 * 8 = 1`
    - Result: `1.01` (1 and 1/8 in fractional format).

## Examples:

### 1. Converting Decimal to Fractional:

```excel
=DOLLARFR(1.125, 8)
```

**Result:** `1.01`

This converts `1.125` into its fractional equivalent of `1` and `1/8` (1.01 when expressed in fractional notation).

---

### 2. Using Sixteenths for Conversion:

```excel
=DOLLARFR(3.25, 16)
```

**Result:** `3.04`

This converts `3.25` into its fractional equivalent of `3` and `4/16` (3.04 in fractional format).

---

### 3. Handling a Custom Denominator:

```excel
=DOLLARFR(10.25, 12)
```

**Result:** `10.03`

This converts `10.25` into its fractional equivalent of `10` and `3/12` (10.03 in fractional format).

## Notes:

- If **fraction** is less than or equal to 0, the function returns a `#NUM!` error.
- If the **decimal_number** contains invalid characters or is improperly formatted, the function returns a `#VALUE!`
  error.
- Ensure that the denominator matches the desired fractional base for accurate results (e.g., 8 for eighths, 16 for
  sixteenths).

## Applications:

- **Stock Price Display**: Frequently used by stock market analysts to represent decimal values in fractional formats.
- **Bond Prices**: Helps convert decimals to a fractional format commonly used in bond trading.
- **Financial Presentations**: Essential for displaying prices or calculations in traditional fractional formats for
  consistency.

> **Tip:** Use `DOLLARFR` in conjunction with `DOLLARDE` to toggle between fractional and decimal formats as needed. For
> example, you can convert a value to a fraction for presentation and back to a decimal for calculations.