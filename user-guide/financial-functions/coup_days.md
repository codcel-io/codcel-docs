<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COUPDAYS Function

The `COUPDAYS` function in Excel is used to calculate the **total number of days in the coupon period that contains the
settlement date** for a bond that pays periodic interest (coupon payments). This function is valuable in financial
calculations related to bonds and accrued interest.

## Key Features of COUPDAYS:

- Determines the total number of days in a coupon period.
- Assists in financial modeling, specifically in bond valuation and interest accrual calculations.
- Supports different day-count conventions with the `basis` parameter.

## Syntax:

```plaintext
COUPDAYS(settlement, maturity, frequency, [basis])
```

- **settlement**: The date when the bond is purchased and settled.
- **maturity**: The maturity date when the bond expires.
- **frequency**: The number of coupon payments per year. Valid values are:
    - `1` = Annual.
    - `2` = Semi-annual.
    - `4` = Quarterly.
- **[basis]**: (Optional) Specifies the day-count convention. Defaults to `0`. Options include:
    - `0` = US (NASD) 30/360 (default).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

## How It Works:

1. Identifies the current coupon period containing the **settlement** date.
2. Calculates the total number of days in that period using the specified day-count basis (**basis**).
3. Returns the result as the number of days.

## Examples:

### 1. Semi-Annual Coupon Bond with Default (30/360) Day Basis:

```excel
=COUPDAYS(DATE(2023,5,15), DATE(2028,5,15), 2)
```

**Result:** The total number of days in the coupon period containing May 15, 2023, assuming a 30/360 day-count
convention.

### 2. Quarterly Coupon Bond Using Actual/365 Day Basis:

```excel
=COUPDAYS(DATE(2024,3,1), DATE(2029,3,1), 4, 3)
```

**Result:** Returns the total days in the coupon period (e.g., 91 or 92 days, depending on the actual/365 calculation).

### 3. Annual Coupon Bond with European 30/360 Day Basis:

```excel
=COUPDAYS(DATE(2025,6,30), DATE(2030,6,30), 1, 4)
```

**Result:** Calculates the total days in the coupon year containing June 30, 2025, using the European 30/360 basis.

## Notes:

- If **settlement** or **maturity** dates are invalid, or if **frequency** is not `1`, `2`, or `4`, Excel will return a
  `#NUM!` or `#VALUE!` error.
- **Settlement** date must be earlier than the **maturity** date; otherwise, an error is returned.
- The **basis** affects the day-count convention:
    - **30/360** methods assume 30 days in each month.
    - **Actual** methods count the actual number of days within periods.
    - **European 30/360** treats all months as 30 days except for special cases.

## Applications:

- **Bond Valuation**: Assists in estimating accrued interest for bonds, especially when determining the time-based
  portion of interest.
- **Financial Modeling**: Provides accurate coupon period day calculations for yield and price modeling.
- **Investment Analysis**: Aids in adjusting returns, payments, and risk models tied to specific coupon periods.

> **Tip:** Combine `COUPDAYS` with other date functions like `DATE()` to avoid manual date entry errors when performing
financial calculations.