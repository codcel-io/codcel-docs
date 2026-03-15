<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COUPDAYSNC Function

The `COUPDAYSNC` function in Excel is used to calculate the **number of days from the settlement date to the next coupon
date** for a bond that pays periodic interest (coupon payments). This function is valuable in bond valuation and accrued
interest computations.

## Key Features of COUPDAYSNC:

- Determines the number of days remaining until the next coupon payment.
- Essential for financial calculations, especially when estimating accrued interest or performing bond pricing.
- Supports different day-count conventions through the optional `basis` parameter.

## Syntax:

```plaintext
COUPDAYSNC(settlement, maturity, frequency, [basis])
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

1. Identifies the coupon period containing the **settlement** date.
2. Calculates the number of days between the **settlement** date and the next scheduled coupon date based on the given *
   *frequency** and **basis**.
3. Returns the computed number of days.

## Examples:

### 1. Semi-Annual Coupon Bond with Default (30/360) Day Basis:

```excel
=COUPDAYSNC(DATE(2023,5,15), DATE(2028,5,15), 2)
```

**Result:** The number of days from May 15, 2023 (settlement date) to the next coupon date, using a 30/360 day-count
convention for semi-annual payments.

### 2. Quarterly Coupon Bond Using Actual/Actual Day Basis:

```excel
=COUPDAYSNC(DATE(2024,7,1), DATE(2029,7,1), 4, 1)
```

**Result:** Returns the number of days from the settlement date (July 1, 2024) to the next coupon date, using the
actual/actual day-count convention.

### 3. Annual Coupon Bond with European 30/360 Day Basis:

```excel
=COUPDAYSNC(DATE(2025,12,15), DATE(2030,12,15), 1, 4)
```

**Result:** Calculates the number of days from December 15, 2025 (settlement date) to the next annual coupon date, using
the European 30/360 basis.

## Notes:

- If **settlement** or **maturity** dates are invalid, or if **frequency** is not `1`, `2`, or `4`, Excel will return a
  `#NUM!` or `#VALUE!` error.
- **Settlement** date must precede the **maturity** date; otherwise, an error is returned.
- The **basis** impacts the calculation method for the number of days:
    - **30/360** methods assume 30 days per month.
    - **Actual** methods count the precise number of days.
    - **European 30/360** treats all months as 30 days except for specific edge cases.

## Applications:

- **Accrued Interest**: Assists in determining the remaining time-based portion of interest payments for coupon bonds.
- **Bond Valuation**: Used in pricing bonds and calculating yield to maturity.
- **Financial Modeling**: Ensures accurate projections for cash flow or interest adjustments tied to coupon payments.

> **Tip:** To avoid errors, ensure date inputs in `COUPDAYSNC` are formatted correctly using date functions like
`DATE()`.