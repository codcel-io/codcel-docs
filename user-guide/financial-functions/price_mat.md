<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PRICEMAT Function

The `PRICEMAT` function in Excel calculates the **price per $100 face value** of a security that pays interest at
maturity. This function is particularly useful for evaluating bonds and similar securities where the principal and
interest are paid together at the end of the investment term.

### Key Features of PRICEMAT:

- Determines the price of securities that pay accrued interest at maturity.
- Accounts for the investment's settlement, maturity, issue date, interest rate, and day count basis.
- Useful for evaluating the cost of interest-bearing securities.

### Syntax:

```plaintext
PRICEMAT(settlement, maturity, issue, rate, yld, [basis])
```

- **settlement**: The date when the security is purchased or settled. Must be a valid date and earlier than the
  *maturity* date.
- **maturity**: The date when the security matures or expires. Must be a valid date and later than the **settlement**
  and **issue** dates.
- **issue**: The date when the security was issued.
- **rate**: The annual coupon interest rate of the security (as a decimal). For example, a 5% rate would be `0.05`.
- **yld**: The annual yield of the security (as a decimal). For example, a 6% yield would be `0.06`.
- **[basis]** *(optional)*: The day count basis to use for the calculation. Defaults to `0` if omitted. Options include:
    - `0` = US (NASD) 30/360
    - `1` = Actual/Actual
    - `2` = Actual/360
    - `3` = Actual/365
    - `4` = European 30/360

### Examples:

1. **Basic Security Pricing**:
   `=PRICEMAT(DATE(2023, 1, 1), DATE(2023, 12, 31), DATE(2022, 1, 1), 0.05, 0.06)`  
   Calculates the price for a security with a 5% annual coupon rate, 6% yield, issued on 1st January 2022, and maturing
   on 31st December 2023.  
   **Result**: `$98.92` (example output may vary).

2. **Using a Different Day Count Basis**:
   `=PRICEMAT(DATE(2023, 1, 1), DATE(2023, 12, 31), DATE(2022, 1, 1), 0.05, 0.06, 3)`  
   Computes the price using Actual/365 day count convention.  
   **Result**: `$98.84`.

3. **Security with Higher Yield**:
   `=PRICEMAT(DATE(2023, 1, 1), DATE(2024, 1, 1), DATE(2022, 1, 1), 0.03, 0.07)`  
   Evaluates a security with a 3% coupon rate and a 7% yield.  
   **Result**: `$95.15`.

### Notes:

- **settlement**, **maturity**, and **issue** dates must be valid, with **issue** preceding **settlement**, and *
  *settlement** preceding **maturity**.
- The **rate** and **yld** inputs are annualized and expressed as decimals (e.g., 5% as `0.05`).
- The **basis** determines how the days between dates are counted for the calculation:
    - For example, the US (NASD) 30/360 basis assumes 30-day months and a 360-day year.
- If no **basis** is given, the default (US 30/360) applies.

> **Tips**:
> - Use `PRICEMAT` to compare the prices of bonds with different interest rates and yields.
> - Combine with functions like `YIELDMAT` to analyze the returns of the securities.
> - Ensure consistent and valid date formats to avoid errors.