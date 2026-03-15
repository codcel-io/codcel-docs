<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ODDLYIELD Function

The `ODDLYIELD` function in Excel calculates the **yield of a security with an odd (irregular) last period**. This is
commonly used for bonds or securities where the last coupon period is shorter or longer than usual.

It is a critical function for financial analysts to evaluate the return (yield) on investments with irregular final
payment schedules, ensuring accurate computation of returns.

---

### Key Features of ODDLYIELD:

- Computes the annual yield for a security with an irregular last coupon period.
- Considers the specific irregularity at the end of the security's lifetime (i.e., non-standard payment durations).
- Useful in financial analysis for accurate yield computation on bonds or securities.

---

### Syntax:

```plaintext
ODDLYIELD(settlement, maturity, last_interest, rate, pr, redemption, frequency, [basis])
```

#### Arguments:

1. **settlement**: The settlement date of the security (the date the buyer acquires it).
    - Must be a valid Excel date.
    - The **settlement date** must occur before the **maturity date**.

2. **maturity**: The maturity date of the security (the date the principal is repaid).
    - Must also be a valid Excel date.

3. **last_interest**: The date of the last interest payment before the maturity date.
    - Determines the irregularity of the last coupon period.

4. **rate**: The annual coupon rate of the security.
    - Represented as a decimal (e.g., 6% is entered as `0.06`).

5. **pr**: The price of the security per $100 of face value.
    - Represents the price paid for the bond or security.

6. **redemption**: The redemption (or face) value per $100 of the security (usually `100`).

7. **frequency**: The number of coupon payments per year.
    - Allowed values:
        - `1`: Annual
        - `2`: Semi-Annual
        - `4`: Quarterly

8. **[basis]** *(optional)*: The day-count basis for interest calculation (default is `0` for US (NASD) 30/360).
    - Possible values:
        - `0`: US (NASD) 30/360 (default)
        - `1`: Actual/Actual
        - `2`: Actual/360
        - `3`: Actual/365
        - `4`: European 30/360

---

### Examples:

1. **Yield Calculation for a Semi-Annual Bond with Odd Last Period**
   ```excel
   =ODDLYIELD(DATE(2023,7,1), DATE(2028,1,15), DATE(2027,7,1), 0.055, 95, 100, 2, 0)
   ```
    - **Bond Details**:
        - Settlement date: `1-Jul-2023`
        - Maturity date: `15-Jan-2028`
        - Last interest payment date: `1-Jul-2027`
        - Annual coupon rate: `5.5%`
        - Price: `$95` per $100 face value
        - Redemption value: `$100`
        - Payment frequency: Semi-Annual (`2`)
        - Day count basis: US (NASD) 30/360 (`0`)
    - **Result**: `6.12%` (example yield).

2. **Yield for Quarterly Bond with an Irregular Last Period**
   ```excel
   =ODDLYIELD(DATE(2023,9,1), DATE(2025,6,30), DATE(2025,3,31), 0.04, 98, 100, 4, 1)
   ```
    - **Bond Details**:
        - Settlement date: `1-Sep-2023`
        - Maturity date: `30-Jun-2025`
        - Last interest payment date: `31-Mar-2025`
        - Annual coupon rate: `4%`
        - Price: `$98` per $100 face value
        - Redemption value: `$100`
        - Payment frequency: Quarterly (`4`)
        - Day count basis: Actual/Actual (`1`)
    - **Result**: `4.35%` (example yield).

---

### Notes:

- **Settlement, maturity, and last_interest dates must be valid Excel dates**:
    - Use Excel's `DATE` function to ensure correct formatting of dates.
    - The settlement date must fall before the maturity date, or Excel will return an error.

- **Irregular last periods**:
    - The `ODDLYIELD` function specifically accounts for securities with irregular final coupon payments, providing
      accurate yield estimations.

- **Interrelation with prices**:
    - The yield (calculated using `ODDLYIELD`) relies on the price (`pr`). Prices higher than face value typically
      reduce the yield, while lower prices increase it.

---

# ODDLYIELD - Codcel vs Excel Compatibility

## Overview

Codcel's `ODDLYIELD` function calculates the yield of a bond with an odd (irregular) last coupon period. It is designed to match Microsoft Excel's behavior and produces identical results for the vast majority of inputs. A small number of edge cases involving February end-of-month boundaries produce results with negligible differences.

## Function Signature

```
ODDLYIELD(settlement, maturity, last_interest, rate, pr, redemption, frequency, [basis])
```

| Parameter | Description |
|-----------|-------------|
| `settlement` | Settlement date of the security |
| `maturity` | Maturity date of the security |
| `last_interest` | Last interest (coupon) date before maturity |
| `rate` | Annual coupon rate |
| `pr` | Price per 100 face value |
| `redemption` | Redemption value per 100 face value |
| `frequency` | Coupon payments per year: 1 (annual), 2 (semi-annual), 4 (quarterly) |
| `basis` | Day count basis (0-4, default 0) |

### Supported Day Count Bases

| Basis | Description |
|-------|-------------|
| 0 | US (NASD) 30/360 |
| 1 | Actual/Actual |
| 2 | Actual/360 |
| 3 | Actual/365 |
| 4 | European 30/360 |

## What Works

Codcel matches Excel exactly across a wide range of scenarios, including:

- **All five day count bases** (0 through 4)
- **All three payment frequencies** (annual, semi-annual, quarterly)
- **Premium bonds** (coupon rate greater than yield)
- **Discount bonds** (yield greater than coupon rate)
- **Zero coupon rate** and **zero yield** bonds (including the trivial rate=0, price=redemption case)
- **Rate equal to yield** scenarios
- **Non-standard redemption values** (e.g. 95, 105, 200)
- **Short and long odd last periods**
- **Settlement close to maturity** or **close to the last interest date**
- **Low and high coupon rates** (0.5% to 15%)

For semi-annual and annual bonds, Codcel produces results identical to Excel regardless of the day count basis used.

## Where Small Differences Can Occur

ODDLYIELD is implemented by solving for the yield that makes ODDLPRICE equal the observed price, using Newton-Raphson root-finding. Any small difference in the underlying ODDLPRICE calculation therefore propagates into ODDLYIELD, amplified by the price-yield sensitivity of the bond.

Differences can arise when **all three** of the following conditions are present simultaneously:

1. **Quarterly frequency** (frequency = 4)
2. **30/360 day count basis** (basis 0 or basis 4)
3. **Coupon periods that cross a February end-of-month boundary** (e.g. the last interest date falls on November 30, August 31, or another month-end that produces a February 28/29 quasi-coupon date)

These are the same edge cases documented in the [ODDLPRICE compatibility notes](odd_l_price.md). The root cause is the inherent non-additivity of 30/360 day count conventions at February boundaries, where Excel uses an undocumented proprietary method to resolve the ambiguity.

### Size of Differences

| Scenario | Maximum Price Difference | Maximum Yield Difference |
|----------|------------------------|-------------------------|
| Basis 0 (US 30/360) with Feb EOM crossing | ~0.03 per 100 face value | ~0.0006 (6 basis points) |
| Basis 4 (European 30/360) with Feb EOM crossing | ~0.0004 per 100 face value | ~0.00001 (0.1 basis points) |

These differences are negligible for practical purposes:

- The largest possible yield difference is approximately **6 basis points** (0.06%), occurring only in the most extreme quarterly basis-0 edge case
- The basis-4 edge case produces a yield difference of only **0.1 basis points**
- These are well within typical bid-ask yield spreads for fixed-income securities
- They would not affect investment decisions, risk calculations, or trade execution
- No known open-source implementation (LibreOffice Calc, Gnumeric, or Python financial libraries) matches Excel exactly for these edge cases either

### How to Avoid Differences Entirely

If exact Excel parity is required for your use case, you can avoid these edge cases by:

- Using **semi-annual** or **annual** frequency instead of quarterly
- Using **basis 1, 2, or 3** (actual-day bases) instead of 30/360 variants
- Choosing last interest dates that do not produce quasi-coupon dates falling on February 28/29

## Technical Background

ODDLYIELD solves the inverse problem of ODDLPRICE: given a bond's price, find the yield. It uses Newton-Raphson iteration with numerical derivatives, calling ODDLPRICE at each step to evaluate the price function:

1. Start with the coupon rate as the initial yield guess (or 5% for zero-coupon bonds)
2. Compute `ODDLPRICE(yield_guess)` and compare to the target price
3. Estimate the derivative `dPrice/dYield` numerically using a central difference
4. Update the yield guess: `yield -= (price_at_guess - target_price) / derivative`
5. Repeat until convergence (tolerance of 1e-12)

Because ODDLYIELD delegates all day-count and quasi-coupon period logic to ODDLPRICE, any edge-case differences in ODDLPRICE are inherited by ODDLYIELD. The price-to-yield amplification factor depends on the bond's duration and convexity: longer-duration or higher-yield bonds amplify small price differences more than shorter-duration or lower-yield bonds.

For the special case where both the coupon rate and the target price equal the redemption value (i.e. a zero-coupon bond priced at par), the yield is trivially zero and is returned without iteration.

### Common Errors:

1. **`#NUM!`**:
    - Occurs when:
        - The settlement date is not earlier than the maturity date.
        - Frequency is invalid (not `1`, `2`, or `4`).
        - Invalid values are used for `rate`, `pr`, or `redemption`.

2. **`#VALUE!`**:
    - Occurs when dates are invalid or other arguments are improperly entered.

> **Tip**: Use `ODDLYIELD` to precisely evaluate the annual returns on bonds or securities with irregular payment
> periods.
---