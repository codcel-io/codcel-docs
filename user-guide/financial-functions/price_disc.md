<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PRICEDISC Function

The `PRICEDISC` function in Excel calculates the **price per $100 face value** of a discounted security, such as a
Treasury bill, that does not pay periodic interest. This function is helpful for evaluating the price of securities that
trade at a discount and mature at their face value.

### Key Features of PRICEDISC:

- Determines the price per $100 face value for a security with no coupon payments.
- Useful for analyzing discount securities like Treasury bills and zero-coupon bonds.
- Incorporates various day count conventions to adapt to different market standards.

### Syntax:

```plaintext
PRICEDISC(settlement, maturity, discount, redemption, [basis])
```

- **settlement**: The date when the security is purchased or settled. Must be a valid date and earlier than the *
  *maturity** date.
- **maturity**: The date when the security matures or expires. Must be a valid date and later than the **settlement**
  date.
- **discount**: The annual discount rate of the security (as a decimal). For example, a 5% discount rate would be
  `0.05`.
- **redemption**: The redemption value (or face value) of the security per $100, typically `100`.
- **[basis]** *(optional)*: The day count basis used to calculate the price. Defaults to `0` if omitted. Options
  include:
    - `0` = US (NASD) 30/360
    - `1` = Actual/Actual
    - `2` = Actual/360
    - `3` = Actual/365
    - `4` = European 30/360

### Examples:

1. **Simple Discount Security**:
   `=PRICEDISC(DATE(2023, 1, 1), DATE(2023, 7, 1), 0.05, 100)`  
   Calculates the price of a discounted security with a 5% discount rate, maturing in 6 months.  
   **Result**: `$97.50`.

2. **Different Day Count Basis**:
   `=PRICEDISC(DATE(2023, 1, 1), DATE(2023, 7, 1), 0.05, 100, 3)`  
   Computes the price using the Actual/365 day count convention for the same security.  
   **Result**: `$97.53`.

3. **Discount and Face Value Variation**:
   `=PRICEDISC(DATE(2023, 1, 1), DATE(2024, 1, 1), 0.03, 150)`  
   Evaluates a 1-year discounted security with a 3% discount rate and a redemption value of $150.  
   **Result**: `$145.73`.

### Notes:

- The **settlement** date must precede the **maturity** date, and both must be valid.
- The **discount** rate is annualized and calculated as a decimal (e.g., 5% is `0.05`).
- The **basis** affects the calculation of days between the **settlement** and **maturity** dates:
    - For example, the US (NASD) 30/360 convention assumes 30-day months and a 360-day year.
- If no **basis** is specified, it defaults to `0` (US 30/360).

> **Tips**:
> - Lower prices reflect higher discounts, and vice versa.
> - Use `PRICEDISC` alongside functions like `YIELDDISC` to compare securities and determine yields.
> - Ensure the date formats for **settlement** and **maturity** are valid; mismatches can cause errors.