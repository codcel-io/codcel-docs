<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COUPNUM Function

The `COUPNUM` function in Excel is used to calculate the **number of coupon payments remaining** between the settlement
date and the maturity date for a bond that pays periodic interest (coupon payments). This is particularly useful in
financial modeling for understanding the remaining lifecycle of a bond.

## Key Features of COUPNUM:

- Returns the total number of coupon payments between the settlement date and the maturity date of a bond.
- Helps assess how many payments are left for budgeting, forecasting, or bond valuation purposes.
- Enables investors and analysts to calculate remaining periods for interest payments.

## Syntax:

```plaintext
COUPNUM(settlement, maturity, frequency, [basis])
```

- **settlement**: The date when the bond is purchased and settled.
- **maturity**: The date when the bond expires.
- **frequency**: The number of coupon payments per year. Valid values are:
    - `1` = Annual.
    - `2` = Semi-annual.
    - `4` = Quarterly.
- **[basis]** (Optional): Specifies the day-count convention. Defaults to `0`. Options include:
    - `0` = US (NASD) 30/360 (default).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

## How It Works:

1. Determines the coupon payment schedule based on the **maturity** date, **frequency**, and optional **basis**.
2. Counts the total number of coupon periods between the **settlement** date (exclusive) and the **maturity** date (
   inclusive).

## Examples:

### 1. Semi-Annual Coupon Bond with Default (30/360) Day Basis:

```excel
=COUPNUM(DATE(2023,5,15), DATE(2028,5,15), 2)
```

**Result:** Returns the total number of coupon payments remaining for a bond with a semi-annual frequency between May
15, 2023, and the maturity date, May 15, 2028.

### 2. Quarterly Coupon Bond Using Actual/360 Day Basis:

```excel
=COUPNUM(DATE(2024,1,1), DATE(2026,1,1), 4, 2)
```

**Result:** Returns the total number of coupon payments remaining for a quarterly bond using the Actual/360 basis,
starting from January 1, 2024, until January 1, 2026.

### 3. Annual Coupon Bond with European 30/360 Day Basis:

```excel
=COUPNUM(DATE(2025,12,15), DATE(2030,12,15), 1, 4)
```

**Result:** Returns the total number of annual coupon payments for a bond that uses the European 30/360 day convention
between December 15, 2025, and December 15, 2030.

## Notes:

- The **settlement** date must precede the **maturity** date, or Excel will return a `#NUM!` error.
- The **frequency** parameter must be `1`, `2`, or `4`. Any other value will result in a `#NUM!` error.
- Excel may return a `#VALUE!` error if the inputs are invalid, such as improperly formatted dates or non-numeric
  frequency.
- The **basis** parameter affects the way the time between payments is calculated, depending on the day-count
  convention.

## Applications:

- **Financial Planning**: Helps investors understand how many coupon payments remain for a bond before its maturity.
- **Bond Valuation**: Necessary to calculate the remaining interest expected from a bond investment.
- **Cash Flow Forecasting**: Useful for projecting cash flows based on the periodic coupon payments during the life of
  the bond.

> **Tip:** Use properly formatted dates (via functions like `DATE()`) for the **settlement** and **maturity** arguments
> to avoid errors. Always double-check the **basis** parameter for compatibility with your specific use case.