<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COUPDAYBS Function

The `COUPDAYBS` function in Excel is used to calculate the **number of days from the beginning of the coupon period to
the settlement date** for a security that pays periodic interest (a coupon bond). This function is particularly useful
in financial analysis, bond valuation, and interest accrual calculations.

## Key Features of COUPDAYBS:

- Calculates the number of days in a specific period for interest accrual purposes.
- Helps investors and analysts assess the amount of time elapsed since the last coupon date.
- Supports various day-count conventions through the optional `basis` argument.

## Syntax:

```plaintext
COUPDAYBS(settlement, maturity, frequency, [basis])
```

- **settlement**: The date when the security is purchased (the settlement date).
- **maturity**: The maturity date of the security.
- **frequency**: The number of coupon payments per year. Valid values are:
    - `1` = Annual.
    - `2` = Semi-annual.
    - `4` = Quarterly.
- **[basis]**: (Optional) The day count basis to use. Defaults to `0`. Options include:
    - `0` = US (NASD) 30/360 (default).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

## How It Works:

1. Identifies the start of the current coupon period based on the **settlement** date.
2. Calculates the number of days between the start of the coupon period and the **settlement** date.
3. Applies the specified day count convention (**basis**) to determine the appropriate result.

## Examples:

### 1. Semi-Annual Coupon Bond with Default (30/360) Day Basis:

```excel
=COUPDAYBS(DATE(2023,5,15), DATE(2028,5,15), 2)
```

**Result:** The number of days from the start of the current coupon period to May 15, 2023, assuming a 30/360 day-count
basis.

### 2. Quarterly Coupon Bond Using Actual/365 Day Basis:

```excel
=COUPDAYBS(DATE(2024,3,1), DATE(2029,3,1), 4, 3)
```

**Result:** Calculates the number of days from the start of the coupon period to March 1, 2024, using an actual/365
day-count convention.

### 3. Annual Coupon Bond with European 30/360 Day Basis:

```excel
=COUPDAYBS(DATE(2025,6,30), DATE(2030,6,30), 1, 4)
```

**Result:** Returns the number of days from the start of the coupon year up to June 30, 2025, using the European 30/360
method.

## Notes:

- If **settlement** or **maturity** dates are invalid or if **frequency** is not `1`, `2`, or `4`, Excel will return a
  `#NUM!` or `#VALUE!` error.
- The **settlement** date must occur before the **maturity** date; otherwise, Excel will return an error.
- The **basis** input affects how days are calculated:
    - **30/360** methods assume 30 days per month.
    - **Actual** methods count the actual number of days in a period.

## Applications:

- **Bond Valuation**: Accurate calculation of accrued interest for bonds traded on secondary markets.
- **Financial Analysis**: Used in yield, price, and risk modeling where time-based coupon calculations are required.
- **Investment Accounting**: Helps allocate income or interest correctly within partial periods.

> **Tip:** Use Excel's built-in `DATE(year, month, day)` function to ensure date inputs are valid, especially for
financial calculations involving complex day-count conventions.