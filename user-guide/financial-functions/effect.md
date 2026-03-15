<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# EFFECT Function

The `EFFECT` function in Excel calculates the **effective annual interest rate** from a given nominal annual interest
rate and the number of compounding periods per year.

This function is particularly helpful when comparing financial products with different nominal rates and compounding
frequencies, allowing for a standardized comparison.

## Key Features of EFFECT:

- Converts a nominal annual interest rate with periodic compounding to an effective annual interest rate.
- Useful for investment and loan comparisons.
- Allows precise analysis of financial schedules and payment impacts.

## Syntax:

```plaintext
EFFECT(nominal_rate, npery)
```

### Arguments:

- **nominal_rate**: The nominal annual interest rate (as a percentage). For example, 5% should be entered as `0.05`.
- **npery**: The number of compounding periods per year:
    - For annual compounding, use `1`.
    - For semi-annual compounding, use `2`.
    - For monthly compounding, use `12`.

## How It Works:

1. The effective annual rate is calculated based on the formula:

   ```plaintext
   EFFECT = (1 + nominal_rate / npery) ^ npery - 1
   ```

2. This function adjusts the nominal rate to include the effects of compounding periods, providing the actual annual
   rate earned or paid.

## Examples:

### 1. Calculate Effective Annual Rate for Monthly Compounding:

```excel
=EFFECT(0.05, 12)
```

**Result:** `0.05116` (or 5.116%)

This calculates the effective annual interest rate for a nominal rate of 5% compounded monthly.

---

### 2. Calculate Effective Annual Rate for Semi-Annual Compounding:

```excel
=EFFECT(0.06, 2)
```

**Result:** `0.0609` (or 6.09%)

This computes the effective rate for a nominal annual interest rate of 6% compounded semi-annually.

---

### Notes:

- If **npery** is less than 1, the function returns a `#NUM!` error.
- **nominal_rate** must be non-negative, or the function will return a `#NUM!` error.
- The function provides accurate results for consistent nominal rates and compounding periods.

## Applications:

- **Loan Comparisons**: Understand the true cost of a loan by comparing effective interest rates rather than nominal
  rates.
- **Investment Analysis**: Standardize yields of different financial instruments with varying compounding schedules.
- **Financial Decision-Making**: Choose between financial products with clarity on the actual annual rate.

> **Tip:** Use the `NOMINAL` function in Excel to calculate the nominal annual rate if you know the effective annual
rate and the compounding frequency.