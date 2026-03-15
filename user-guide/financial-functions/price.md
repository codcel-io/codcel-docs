<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PRICE Function

The `PRICE` function in Excel calculates the **price per $100 face value** of a security that pays periodic interest,
based on settlement and maturity dates, annual coupon rate, yield, and day count convention. This function helps in
determining the value of a bond or similar financial instrument.

### Key Features of PRICE:

- Computes the price of a bond per $100 of face value based on its financial details.
- Essential for analyzing bond investments and comparing yields.
- Considers a variety of day count conventions to adjust calculations for varying market standards.

### Syntax:

```plaintext
PRICE(settlement, maturity, rate, yld, redemption, frequency, [basis])
```

- **settlement**: The date on which the bond/security is purchased or settled. Must be later than the issue date.
- **maturity**: The date on which the bond/security expires or matures.
- **rate**: The annual coupon rate of the security (expressed as a decimal). For example, a 5% annual coupon rate would
  be `0.05`.
- **yld**: The annual yield of the bond/security (expressed as a decimal). For example, a 6% annual yield would be
  `0.06`.
- **redemption**: The redemption (or face) value of the bond per $100, typically `100`.
- **frequency**: The number of coupon payments per year. Valid options are:
    - `1` = Annual payments
    - `2` = Semiannual payments
    - `4` = Quarterly payments
- **[basis]** *(optional)*: The day count basis to use for the calculation. Defaults to `0` if omitted. Options include:
    - `0` = US (NASD) 30/360
    - `1` = Actual/Actual
    - `2` = Actual/360
    - `3` = Actual/365
    - `4` = European 30/360

### Examples:

1. **Simple Bond Price**:
   `=PRICE(DATE(2023, 1, 1), DATE(2033, 1, 1), 0.05, 0.06, 100, 2)`  
   Calculates the price of a 10-year semiannual bond with a 5% coupon rate and a 6% yield.  
   **Result**: `$92.64` (bond price reflects a discount due to yield > coupon).

2. **Quarterly Coupon Payments**:
   `=PRICE(DATE(2023, 1, 1), DATE(2030, 1, 1), 0.04, 0.035, 100, 4)`  
   Computes the price of a bond with quarterly interest payments, a 7-year maturity, a 4% coupon rate, and a 3.5%
   yield.  
   **Result**: `$103.18` (bond price reflects a premium due to yield < coupon).

3. **Customized Basis**:
   `=PRICE(DATE(2023, 1, 1), DATE(2028, 1, 1), 0.045, 0.05, 100, 2, 1)`  
   Computes the price of a 5-year semiannual bond using Actual/Actual day count convention, with a 4.5% coupon rate and
   a 5% yield.  
   **Result**: `$98.47`.

### Notes:

- The **settlement** date represents the date when the buyer acquires the security. It must occur before the **maturity
  ** date.
- The **rate** (coupon) and **yld** (yield) should represent their annual values as decimals.
- The **basis** day count convention affects how interest and payment periods are calculated:
    - For example, the US 30/360 method assumes a year has 360 days divided into 12 months of 30 days each.
- If the **frequency** does not match the bond, results may be inaccurate.

> **Tips**:
> - A bond trades at a **discount** if **yld > rate**, and at a **premium** if **yld < rate**.
> - Use `PRICE` alongside `YIELD` to analyze the price-yield relationship of a bond investment.
> - Ensure correct date formats for **settlement** and **maturity** to avoid calculation errors.