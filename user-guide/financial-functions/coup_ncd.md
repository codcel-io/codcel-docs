<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COUPNCD Function

The `COUPNCD` function in Excel is used to calculate the **next coupon date after the settlement date** for a bond that
pays periodic interest (coupon payments). This function is especially useful in financial modeling to determine future
payment schedules for bond investments.

## Key Features of COUPNCD:

- Returns the date of the next coupon payment following the settlement date.
- Useful for tracking bond payment schedules and forecasting cash flows.
- Facilitates precise bond valuation and financial planning by determining exact coupon payment dates.

## Syntax:

```plaintext
COUPNCD(settlement, maturity, frequency, [basis])
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

1. Identifies the coupon schedule determined by the **maturity** date, **frequency**, and optional **basis**.
2. Finds the first coupon date that occurs **after** the given **settlement** date.
3. Returns the date of the next coupon payment from the settlement date.

## Examples:

### 1. Semi-Annual Coupon Bond with Default (30/360) Day Basis:

```excel
=COUPNCD(DATE(2023,5,15), DATE(2028,5,15), 2)
```

**Result:** Returns the next coupon date after May 15, 2023, using a semi-annual schedule with the 30/360 day-count
convention.

### 2. Quarterly Coupon Bond Using Actual/360 Day Basis:

```excel
=COUPNCD(DATE(2024,7,1), DATE(2029,7,1), 4, 2)
```

**Result:** Returns the next coupon date after July 1, 2024, for a quarterly payment schedule using the Actual/360
convention.

### 3. Annual Coupon Bond with European 30/360 Day Basis:

```excel
=COUPNCD(DATE(2025,12,15), DATE(2030,12,15), 1, 4)
```

**Result:** Returns the next coupon date after December 15, 2025, for an annual payment schedule with the European
30/360 basis.

## Notes:

- If **settlement** or **maturity** dates are invalid, Excel will return a `#NUM!` or `#VALUE!` error.
- The **settlement** date must occur before the **maturity** date; otherwise, the function will result in an error.
- The **frequency** parameter must be `1`, `2`, or `4`; otherwise, Excel will return a `#NUM!` error.
- The **basis** parameter affects how the lengths of coupon periods are calculated (e.g., 30-day months for 30/360 vs.
  actual days for Actual/actual).

## Applications:

- **Bond Payment Monitoring**: Helps in maintaining schedules for upcoming coupon payments.
- **Cash Flow Forecasting**: Useful for managing expected cash inflows from bond investments.
- **Financial Planning**: Assists in determining accurate dates for upcoming coupon payments for budgeting and
  investment analysis.

> **Tip:** When using `COUPNCD`, ensure your date inputs are formatted correctly with date-related functions like
`DATE()` to avoid errors.