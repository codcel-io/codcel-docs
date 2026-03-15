<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NOMINAL Function

The `NOMINAL` function in Excel calculates the **nominal annual interest rate** based on the effective annual interest
rate and the number of compounding periods per year. It is commonly used in financial analysis to convert between
effective interest rates and nominal rates.

This function is particularly useful when comparing investments or loans with different compounding methods or when
analyzing nominal versus effective yields.

---

### Key Features of NOMINAL:

- Converts the effective annual interest rate to the nominal annual interest rate.
- Useful for understanding the stated (nominal) rate of financial instruments with various compounding frequencies.
- Often paired with the `EFFECT` function, which performs the inverse operation.

---

### Syntax:

```plaintext
NOMINAL(effect_rate, npery)
```

- **effect_rate**: The effective annual interest rate.
    - Must be provided as a decimal (e.g., 5% = 0.05).
    - It represents the actual interest rate considering the effect of compounding.
- **npery**: The number of compounding periods per year.
    - Must be a positive integer (e.g., 1 = annual, 4 = quarterly, 12 = monthly, etc.).

---

### Examples:

1. `=NOMINAL(0.05, 12)`  
   Converts an effective annual interest rate of 5% with monthly compounding (12 periods per year) into its nominal
   counterpart.  
   **Result**: `4.89%` *(example value).*

2. `=NOMINAL(0.08, 4)`  
   Calculates the nominal interest rate for an effective annual rate of 8% with quarterly compounding.  
   **Result**: `7.72%` *(example value).*

3. `=NOMINAL(0.10, 1)`  
   Finds the nominal interest rate for a 10% effective annual rate with annual compounding. In this case, it will return
   the same value as the effective rate.  
   **Result**: `10.00%`.

---

### Notes:

- The **effect_rate** must be greater than 0, and the **npery** must be a positive integer, or else the function will
  return an error (`#NUM!`).
- The nominal annual rate is always less than or equal to the effective annual rate for multiple compounding periods per
  year.
- For **npery = 1** (annual compounding), the nominal and effective rates will be identical.
- To calculate the effective interest rate from a nominal interest rate, use the `EFFECT` function.

> **Tip**: Use the `NOMINAL` function when you want to present interest rates in a format commonly seen in financial
> documents. It is especially useful when working with rates specified in different compounding frequencies.

---