<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RECEIVED Function

The `RECEIVED` function in Excel calculates the **amount received at maturity** for a fully invested security. This
function is typically used to determine the maturity value of a security or bond based on its issue price, discount
rate, and term to maturity.

### Key Features of RECEIVED:

- Computes the total amount an investor will receive at the maturity of the security.
- Accounts for settlement and maturity dates, ensuring accurate calculation of interest or discount-based returns.
- Ideal for analyzing returns on investments like treasury bills, bonds, or other discount securities.

### Syntax:

```plaintext
RECEIVED(settlement, maturity, investment, discount, [basis])
```

- **settlement**: The date when the security is purchased or settled. This is the **start date** of the investment.
- **maturity**: The date when the security matures and the investor receives the payment. This must be after the
  settlement date.
- **investment**: The amount invested or the initial price paid for the security.
- **discount**: The annual discount rate of the security (as a decimal or percentage).
- **[basis]** *(optional)*: The day count basis used to calculate the interest. Defaults to `0` (US 30/360 convention)
  if omitted. Possible values:
    - `0`: US (NASD) 30/360.
    - `1`: Actual/actual.
    - `2`: Actual/360.
    - `3`: Actual/365.
    - `4`: European 30/360.

### Examples:

1. **Basic Maturity Amount Calculation**:
   `=RECEIVED(DATE(2023, 1, 1), DATE(2023, 12, 31), 1000, 5%)`  
   Calculates the maturity value of a $1,000 investment with a 5% discount rate over one year (using default day count
   basis: 30/360).  
   **Result**: `1052.63`

2. **Specified Day Count Basis**:
   `=RECEIVED(DATE(2023, 1, 1), DATE(2023, 6, 30), 500, 4%, 1)`  
   Computes the amount received for a $500 investment over 6 months with a 4% discount rate, using the actual/actual day
   count basis.  
   **Result**: `510.04`

3. **Custom Duration with European 30/360 Basis**:
   `=RECEIVED(DATE(2023, 4, 1), DATE(2024, 4, 1), 2000, 6%, 4)`  
   Determines the maturity value for a $2,000 investment over 1 year at a 6% discount rate, using the European 30/360
   convention.  
   **Result**: `2127.66`

### Notes:

- **Dates must be entered correctly**:
    - Use the `DATE` function (e.g., `DATE(2023, 1, 1)`) or ensure your date values are valid Excel date formats.
- The **settlement** date must always precede the **maturity** date, or the function will return a `#NUM!` error.
- The **basis** determines how days between settlement and maturity are counted. Choose the appropriate basis for your
  calculation to reflect the correct valuation.
- The **discount rate** is applied annually. For shorter- or longer-term periods, the function adjusts the calculation
  based on the dates and the day count basis.

> **Tips**:
> - Use the `RECEIVED` function to project cash flows from fixed-income securities like bonds or treasury bills.
> - Combine this function with `PRICE`, `YIELD`, or `ACCRINT` for comprehensive financial analysis.
> - Ensure consistent date formats and proper alignment between investment assumptions to avoid calculation errors.