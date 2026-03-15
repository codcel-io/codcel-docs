<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MDURATION Function

The `MDURATION` function in Excel calculates the **Modified Duration** of a security with a fixed interest rate, such as
a bond. Modified duration measures the price sensitivity of a bond to interest rate changes, providing a critical tool
for understanding the bond’s interest rate risk.

This function is particularly valuable in financial analysis for portfolio management and managing interest rate-related
risks.

### Key Features of MDURATION:

- Calculates the Modified Duration, which accounts for the effect of compounding.
- Useful for measuring how a bond’s price changes with respect to interest rate changes.
- Commonly used in fixed-income investing and risk management.

### Syntax:

```plaintext
MDURATION(settlement, maturity, coupon, yld, frequency, [basis])
```

- **settlement**: The settlement date of the security (the date after issuance when the buyer purchases the security).
- **maturity**: The maturity date of the security (the date when the principal is repaid).
- **coupon**: The annual coupon rate (interest rate) expressed as a decimal.
- **yld**: The annual yield of the security (return earned by investors).
- **frequency**: The number of coupon payments per year (e.g., 1 for annual, 2 for semi-annual, 4 for quarterly).
- **basis** *(optional)*: The day-count basis to use. It defaults to 0 (US 30/360 format), but you can specify other
  day-count conventions:
    - `0`: US (NASD) 30/360
    - `1`: Actual/Actual
    - `2`: Actual/360
    - `3`: Actual/365
    - `4`: European 30/360

### Examples:

1. `=MDURATION(DATE(2023,1,1), DATE(2033,1,1), 0.05, 0.045, 2, 0)`  
   Calculates the Modified Duration for a bond with a settlement date of January 1, 2023, a maturity date of January 1,
   2033, a 5% annual coupon rate, a 4.5% annual yield, semi-annual payments (frequency 2), and US (NASD) 30/360 day
   count basis.  
   **Result**: `7.85` *(example value; actual result depends on calculation)*

2. `=MDURATION(DATE(2024,6,15), DATE(2029,6,15), 0.03, 0.035, 1, 1)`  
   Computes the Modified Duration for a bond issued with an annual coupon rate of 3%, an annual yield of 3.5%, annual
   payment frequency, and Actual/Actual day count convention.  
   **Result**: `4.26` *(example value)*

3. `=MDURATION(DATE(2025,4,1), DATE(2030,4,1), 0.04, 0.045, 4, 2)`  
   Calculates the Modified Duration for a bond with quarterly payments, a 4% annual coupon rate, 4.5% annual yield, and
   Actual/360 day count basis.  
   **Result**: `4.93` *(example value)*

### Notes:

- The **settlement** date must be earlier than the **maturity** date; otherwise, the function will return an error (
  `#NUM!`).
- The **frequency** parameter should match the bond's payment schedule (e.g., 1 for annual payments, 2 for semi-annual
  payments, etc.).
- Ensure that the **coupon**, **yld**, and **frequency** are consistent—for example, don’t mix annual coupon rates with
  semi-annual frequencies without appropriate conversion.
- The Modified Duration calculated reflects the approximate percentage change in price for a 1% change in yield.

> **Tip**: Use `MDURATION` alongside other functions like `DURATION` for comprehensive bond analysis and to measure both
price and reinvestment risks when interest rates shift.