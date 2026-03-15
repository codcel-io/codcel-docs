<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ODDLPRICE Function

The `ODDLPRICE` function in Excel calculates the **price per $100 face value** of a security with an **odd (irregular)
last period**. This is particularly useful when working with bonds or securities where the last coupon period is not of
standard length.

It helps financial analysts determine the value of securities that have an irregular final payment period, ensuring
precise pricing analysis for such instruments.

---

### Key Features of ODDLPRICE:

- Calculates the price of a security with an irregular last coupon period.
- Takes into account factors like settlement date, maturity date, coupon rate, redemption value, and more.
- Useful for financial modeling when dealing with bonds or securities with irregular periods at the end of their
  lifetime.

---

### Syntax:

```plaintext
ODDLPRICE(settlement, maturity, last_interest, rate, yld, redemption, frequency, [basis])
```

#### Arguments:

1. **settlement**: The settlement date of the security (the date the buyer acquires it).
    - Must be a valid Excel date.
    - The settlement date must occur before the maturity date.

2. **maturity**: The maturity date of the security (the date the principal is repaid).
    - Must also be a valid Excel date.

3. **last_interest**: The date of the last interest payment.
    - Specifies the irregularity of the last period.

4. **rate**: The annual coupon rate of the security.
    - Enter as a decimal (e.g., 5% is entered as `0.05`).

5. **yld**: The annual yield of the security.
    - The anticipated yield based on the price paid for the bond.

6. **redemption**: The redemption (or face) value per $100 of the security (usually `100`).

7. **frequency**: Number of coupon payments per year.
    - Allowed values are:
        - `1`: Annual
        - `2`: Semi-Annual
        - `4`: Quarterly

8. **[basis]** *(optional)*: The day-count basis for calculating interest (default is `0` for US (NASD) 30/360).
    - Possible values:
        - `0`: US (NASD) 30/360 (default)
        - `1`: Actual/Actual
        - `2`: Actual/360
        - `3`: Actual/365
        - `4`: European 30/360

---

### Examples:

1. **Price for a Semi-Annual Bond with an Odd Last Period**
   ```excel
   =ODDLPRICE(DATE(2023,7,1), DATE(2028,1,15), DATE(2027,7,1), 0.045, 0.05, 100, 2, 0)
   ```
    - **Bond Details**:
        - Settlement date: `1-Jul-2023`
        - Maturity date: `15-Jan-2028`
        - Last interest payment: `1-Jul-2027`
        - Coupon rate: `4.5%`
        - Yield: `5%`
        - Redemption value: `$100`
        - Payment frequency: Semi-Annual (`2`)
        - Day count basis: US (NASD) 30/360 (`0`)
    - **Result**: `$98.97` (example value).

2. **Price for Quarterly Bond with Irregular Last Period**
   ```excel
   =ODDLPRICE(DATE(2023,11,1), DATE(2026,3,30), DATE(2025,12,30), 0.03, 0.035, 100, 4, 1)
   ```
    - **Bond Details**:
        - Settlement date: `1-Nov-2023`
        - Maturity date: `30-Mar-2026`
        - Last interest payment: `30-Dec-2025`
        - Coupon rate: `3%`
        - Yield: `3.5%`
        - Redemption value: `$100`
        - Payment frequency: Quarterly (`4`)
        - Day count basis: Actual/Actual (`1`)
    - **Result**: `$99.41` (example value).

---

### Notes:

- **Settlement, maturity, and last_interest dates must be valid Excel dates**:
    - Use Excel's `DATE` function to properly format dates.
    - The settlement date must be before the maturity date, or Excel will return `#NUM!`.

- **Irregular last periods**:
    - The `ODDLPRICE` function specifically addresses scenarios where the last coupon payment period deviates from
      typical intervals, ensuring calculated prices reflect reality.

- **Related Financial Functions**:
    - Combine with `ODDLPRICE` and other financial functions to analyze securities with irregular payment periods.

---

# ODDLPRICE - Codcel vs Excel Compatibility

## Overview

Codcel's `ODDLPRICE` function calculates the price of a bond with an odd (irregular) last coupon period. It is designed to match Microsoft Excel's behavior and produces identical results for the vast majority of inputs. A small number of edge cases involving February end-of-month boundaries produce results with negligible differences.

## Function Signature

```
ODDLPRICE(settlement, maturity, last_interest, rate, yld, redemption, frequency, [basis])
```

| Parameter | Description |
|-----------|-------------|
| `settlement` | Settlement date of the security |
| `maturity` | Maturity date of the security |
| `last_interest` | Last interest (coupon) date before maturity |
| `rate` | Annual coupon rate |
| `yld` | Annual yield |
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
- **Zero coupon rate** and **zero yield** bonds
- **Rate equal to yield** scenarios
- **Non-standard redemption values** (e.g. 95, 105, 200)
- **Short and long odd last periods**
- **Settlement close to maturity** or **close to the last interest date**
- **Low and high coupon rates** (0.5% to 15%)

For semi-annual and annual bonds, Codcel produces results identical to Excel regardless of the day count basis used.

## Where Small Differences Can Occur

Very small differences from Excel can arise when **all three** of the following conditions are present simultaneously:

1. **Quarterly frequency** (frequency = 4)
2. **30/360 day count basis** (basis 0 or basis 4)
3. **Coupon periods that cross a February end-of-month boundary** (e.g. the last interest date falls on November 30, August 31, or another month-end that produces a February 28/29 quasi-coupon date)

When these conditions coincide, the 30/360 day count conventions have an inherent ambiguity at the February boundary. For example, with US 30/360 (basis 0):

- Counting days from Nov 30 to May 31 directly gives 180
- Counting Nov 30 to Feb 28 (90) plus Feb 28 to May 31 (91) gives 181

This non-additivity means the day count result depends on whether you compute it as a single span or split it at intermediate dates. Excel uses a proprietary internal method to resolve this ambiguity that is not documented in the published ECMA-376 / MS-OI29500 specification.

### Size of Differences

| Scenario | Maximum Difference | As Percentage |
|----------|-------------------|---------------|
| Basis 0 (US 30/360) with Feb EOM crossing | ~0.03 per 100 face value | ~0.03% |
| Basis 4 (European 30/360) with Feb EOM crossing | ~0.0004 per 100 face value | ~0.0004% |

These differences are negligible for practical purposes:

- The largest possible difference is approximately **3 cents per $100 face value**
- This is well within typical bid-ask spreads for fixed-income securities
- It would not affect pricing decisions, risk calculations, or trade execution
- No known open-source implementation (LibreOffice Calc, Gnumeric, or Python financial libraries) matches Excel exactly for these edge cases either

### How to Avoid Differences Entirely

If exact Excel parity is required for your use case, you can avoid these edge cases by:

- Using **semi-annual** or **annual** frequency instead of quarterly
- Using **basis 1, 2, or 3** (actual-day bases) instead of 30/360 variants
- Choosing last interest dates that do not produce quasi-coupon dates falling on February 28/29

## Technical Background

The ODDLPRICE formula decomposes the odd last period into quasi-coupon sub-periods and computes three values for each:

- **A** - accrued days from period start to settlement
- **DSC** - days from settlement to period end (used for discounting)
- **DC** - total days in the coupon period (used for coupon earned)

For actual-day bases (1, 2, 3), these values are straightforward calendar day counts and are always consistent. For 30/360 bases (0 and 4), the day count conventions apply adjustment rules (e.g. changing day 31 to 30) that can produce different results depending on whether a date span is computed directly or via intermediate dates. The February end-of-month boundary is where these adjustment rules interact most unpredictably, because February 28 (or 29) is treated differently from day 30 or 31 by the adjustment logic.

Codcel uses several techniques to maximise compatibility with Excel for these cases, including YEARFRAC-ordered day count rules and conditional derivation of DSC from DC and A. These techniques resolve the ambiguity correctly for the vast majority of February boundary scenarios, with only a tiny residual difference in the most extreme cases.


### Common Errors:

1. **`#NUM!`**:
    - Occurs when:
        - The settlement date is not earlier than the maturity date.
        - Frequency is invalid or unsupported.

2. **`#VALUE!`**:
    - Occurs if dates or other arguments are invalid or unrecognized.

> **Tip**: Use `ODDLPRICE` to price bonds or securities with irregular last payment schedules accurately within your
> financial models.
---