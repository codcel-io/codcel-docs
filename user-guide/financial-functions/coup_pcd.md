<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# COUPPCD Function

The `COUPPCD` function in Excel is used to calculate the **previous coupon date** before the settlement date for a bond
that pays periodic interest (coupon payments). This function helps in financial modeling to determine the most recent
coupon payment date relative to the bond's settlement date.

## Key Features of COUPPCD:

- Returns the date of the most recent coupon payment **prior to** the specified settlement date.
- Useful in bond valuation and cash flow analysis to account for the time elapsed since the last interest payment.
- Enables precise calculations of accrued interest or cash flows related to bonds.

## Syntax:

```plaintext
COUPPCD(settlement, maturity, frequency, [basis])
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
2. Identifies the most recent coupon payment date **before** the given **settlement** date.

## Examples:

### 1. Semi-Annual Coupon Bond with Default (30/360) Day Basis:

```excel
=COUPPCD(DATE(2023,10,15), DATE(2028,5,15), 2)
```

**Result:** Returns the previous coupon payment date for a semi-annual bond with a maturity date of May 15, 2028,
relative to the settlement date of October 15, 2023.

### 2. Quarterly Coupon Bond Using Actual/360 Day Basis:

```excel
=COUPPCD(DATE(2024,2,15), DATE(2026,2,15), 4, 2)
```

**Result:** Returns the previous coupon date for a quarterly bond with an Actual/360 day basis, with a settlement date
of February 15, 2024, and ending at February 15, 2026.

### 3. Annual Coupon Bond with European 30/360 Day Basis:

```excel
=COUPPCD(DATE(2025,7,1), DATE(2030,7,1), 1, 4)
```

**Result:** Returns the previous coupon date for an annual bond using the European 30/360 convention, with a settlement
date of July 1, 2025.

## Notes:

- The **settlement** date must precede the **maturity** date, or Excel will return a `#NUM!` error.
- The **frequency** parameter must be `1`, `2`, or `4`. Any other value will result in a `#NUM!` error.
- Excel may return a `#VALUE!` error if the inputs are invalid, such as improperly formatted dates or non-numeric
  frequency.
- The **basis** parameter affects how the calculation of days and coupon periods is handled.

## Applications:

- **Accrued Interest Calculations**: Helps determine how much interest has accrued since the last coupon payment.
- **Bond Pricing Models**: Useful for calculating exact payment schedules for bond cash flows.
- **Financial Analysis**: Provides insights into bond payment schedules, useful in financial planning and reporting.

> **Tip:** For reliable results, use properly formatted dates (via functions like `DATE()`) and ensure you provide valid
inputs for all parameters.