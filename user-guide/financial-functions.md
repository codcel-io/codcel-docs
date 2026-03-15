<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# Financial Functions

This contains the list of financial functions that are currently supported by Codcel.

## A

### [ACCRINT](./financial-functions/accr_int.md)
Calculates the accrued interest for a security that pays periodic interest.

- **Purpose:** Useful for determining the interest earned but not yet received, which is often used in fixed-income
  securities trading.

- **Formula:** `ACCRINT(issue, first_interest, settlement, rate, par, frequency, [basis])`
    - `issue` is the date the security was issued.
    - `first_interest` is the date of the first interest payment.
    - `settlement` is the settlement date of the security.
    - `rate` is the annual coupon rate of the security.
    - `par` is the face value of the security (default is 1000).
    - `frequency` is the number of interest payments per year (1 = annual, 2 = semi-annual, 4 = quarterly).
    - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
    - `=ACCRINT(DATE(2023,1,1), DATE(2023,7,1), DATE(2023,9,30), 0.05, 1000, 2)` calculates the accrued interest for a
      semi-annual bond with a 5% coupon rate and a face value of 1000.
    - `=ACCRINT(A1, A2, A3, A4, A5, A6, 1)` computes the accrued interest using cell references for issue date, first
      payment date, settlement date, rate, par, and frequency, with an actual/actual day count basis.

### [ACCRINTM](./financial-functions/accr_intm.md)
Calculates the accrued interest for a security that pays interest at maturity.

- **Purpose:** Useful for determining the interest earned but not yet received for securities that pay interest only at
  maturity.

- **Formula:** `ACCRINTM(issue, maturity, rate, par, [basis])`
  - `issue` is the date the security was issued.
  - `maturity` is the maturity date of the security.
  - `rate` is the annual coupon rate of the security.
  - `par` is the face value of the security (default is 1000).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=ACCRINTM(DATE(2023,1,1), DATE(2025,1,1), 0.05, 1000)` calculates the accrued interest for a bond issued on January
    1, 2023, maturing on January 1, 2025, with a 5% annual coupon rate and a face value of 1000.
  - `=ACCRINTM(A1, A2, A3, A4, 1)` computes the accrued interest using cell references for issue date, maturity date,
    rate, and par, with an actual/actual day count basis.

### [AMORLINC](./financial-functions/amor_linc.md)
Calculates the depreciation for each accounting period using the linear depreciation method.

- **Purpose:** This function is used for calculating uniform depreciation of an asset over its useful life.

- **Formula:** `AMORLINC(cost, date_purchased, first_period, salvage, period, rate, [basis])`
  - `cost` is the initial cost of the asset.
  - `date_purchased` is the date the asset was purchased.
  - `first_period` is the end date of the first period.
  - `salvage` is the value of the asset at the end of the depreciation.
  - `period` is the accounting period number for which the depreciation is calculated.
  - `rate` is the rate of depreciation.
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=AMORLINC(10000, DATE(2023,1,1), DATE(2023,12,31), 1000, 1, 0.1)` calculates the linear depreciation for the first
    year of an asset with an initial cost of 10,000, a salvage value of 1,000, and a depreciation rate of 10%.
  - `=AMORLINC(A1, A2, A3, A4, A5, A6, 1)` computes the depreciation using cell references for cost, purchase date,
    first period end date, salvage value, period, rate, with an actual/actual day count basis.

### [AMORDEGRC](./financial-functions/amor_degrc.md)
Calculates the depreciation for an accounting period using a declining balance method with a specific depreciation
coefficient.

- **Purpose:** This function is helpful for determining accelerated depreciation over an asset's life, often used for
  tax purposes.

- **Formula:** `AMORDEGRC(cost, date_purchased, first_period, salvage, period, rate, depreciation_coef, [basis])`
  - `cost` is the initial cost of the asset.
  - `date_purchased` is the date the asset was purchased.
  - `first_period` is the end date of the first period.
  - `salvage` is the value of the asset at the end of its useful life.
  - `period` is the accounting period number for which the depreciation is calculated.
  - `rate` is the rate of depreciation.
  - `depreciation_coef` is the depreciation coefficient, which increases the rate of depreciation (commonly set to 1.5
    or 2).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=AMORDEGRC(10000, DATE(2023,1,1), DATE(2023,12,31), 1000, 1, 0.2, 2)` calculates the accelerated depreciation for
    the first year of an asset with an initial cost of 10,000, a salvage value of 1,000, a depreciation rate of 20%, and
    a coefficient of 2.
  - `=AMORDEGRC(A1, A2, A3, A4, A5, A6, A7, 1)` computes the depreciation using cell references for cost, purchase date,
    first period end date, salvage value, period, rate, coefficient, and with an actual/actual day count basis.

## C

### [COUPDAYBS](./financial-functions/coup_day_bs.md)
Calculates the number of days from the beginning of the coupon period to the settlement date.

- **Purpose:** This function is essential for determining the elapsed time in a coupon period, often used in bond
  calculations.

- **Formula:** `COUPDAYBS(settlement, maturity, frequency, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `frequency` is the number of coupon payments per year (1 = annual, 2 = semi-annual, 4 = quarterly).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=COUPDAYBS(DATE(2023,1,15), DATE(2028,12,31), 2)` computes the number of days between the beginning of the coupon
    period and the settlement date for a semi-annual bond maturing at the end of 2028.
  - `=COUPDAYBS(A1, A2, A3, 1)` calculates the days using cell references for settlement date, maturity date, and
    frequency, with an actual/actual day count basis.

### [COUPDAYS](./financial-functions/coup_days.md)
Calculates the number of days in the coupon period that contains the settlement date.

- **Purpose:** This function is useful for determining the total number of days in a coupon period, often required in
  bond calculations.

- **Formula:** `COUPDAYS(settlement, maturity, frequency, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `frequency` is the number of coupon payments per year (1 = annual, 2 = semi-annual, 4 = quarterly).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=COUPDAYS(DATE(2023,1,15), DATE(2028,12,31), 2)` computes the total number of days in the coupon period for a
    semi-annual bond maturing at the end of 2028.
  - `=COUPDAYS(A1, A2, A3, 1)` calculates the days using cell references for settlement date, maturity date, and
    frequency, with an actual/actual day count basis.

### [COUPDAYSNC](./financial-functions/coup_days_nc.md)
Calculates the number of days from the settlement date to the next coupon date.

- **Purpose:** This function is useful for determining the remaining time in a coupon period, often used in bond
  calculations.

- **Formula:** `COUPDAYSNC(settlement, maturity, frequency, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `frequency` is the number of coupon payments per year (1 = annual, 2 = semi-annual, 4 = quarterly).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=COUPDAYSNC(DATE(2023,1,15), DATE(2028,12,31), 2)` computes the number of days from the settlement date to the next
    coupon date for a semi-annual bond maturing at the end of 2028.
  - `=COUPDAYSNC(A1, A2, A3, 1)` calculates the days using cell references for settlement date, maturity date, and
    frequency, with an actual/actual day count basis.

### [COUPNCD](./financial-functions/coup_ncd.md)
Calculates the next coupon date after the settlement date.

- **Purpose:** This function is crucial for determining the next payment date for bonds with periodic coupon payments.

- **Formula:** `COUPNCD(settlement, maturity, frequency, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `frequency` is the number of coupon payments per year (1 = annual, 2 = semi-annual, 4 = quarterly).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=COUPNCD(DATE(2023,1,15), DATE(2028,12,31), 2)` calculates the next coupon date after the settlement date for a
    semi-annual bond maturing at the end of 2028.
  - `=COUPNCD(A1, A2, A3, 1)` calculates the next coupon date using cell references for settlement date, maturity date,
    and frequency, with an actual/actual day count basis.

### [COUPNUM](./financial-functions/coup_num.md)
Calculates the number of coupon payments between the settlement date and the maturity date.

- **Purpose:** This function is crucial for determining the total number of coupon payments for a bond over its
  remaining life.

- **Formula:** `COUPNUM(settlement, maturity, frequency, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `frequency` is the number of coupon payments per year (1 = annual, 2 = semi-annual, 4 = quarterly).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=COUPNUM(DATE(2023,1,15), DATE(2028,12,31), 2)` calculates the total number of semi-annual coupon payments from the
    settlement date to the maturity date for a bond maturing at the end of 2028.
  - `=COUPNUM(A1, A2, A3, 1)` computes the total coupon payments using cell references for settlement date, maturity
    date, frequency, with an actual/actual day count basis.

### [COUPPCD](./financial-functions/coup_pcd.md)
Calculates the previous coupon date before the settlement date.

- **Purpose:** This function is essential for determining the coupon payment date immediately preceding the settlement
  date, often used in bond calculations.

- **Formula:** `COUPPCD(settlement, maturity, frequency, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `frequency` is the number of coupon payments per year (1 = annual, 2 = semi-annual, 4 = quarterly).
  - `basis` (optional) is the day-count basis to use (0 = 30/360, 1 = actual/actual, 2 = actual/360, etc.).

- **Example Usage:**
  - `=COUPPCD(DATE(2023,1,15), DATE(2028,12,31), 2)` calculates the previous coupon date before the settlement date for
    a semi-annual bond maturing at the end of 2028.
  - `=COUPPCD(A1, A2, A3, 1)` calculates the previous coupon date using cell references for settlement date, maturity
    date, and frequency, with an actual/actual day count basis.

### [CUMIPMT](./financial-functions/cum_i_pmt.md)
Calculates the cumulative interest paid on a loan or an investment between two periods.

- **Purpose:** This function is essential for determining the total interest paid over a specified range of payments,
  which is useful in financial analysis and loan management.

- **Formula:** `CUMIPMT(rate, nper, pv, start_period, end_period, type)`
  - `rate` is the annual interest rate of the loan or investment.
  - `nper` is the total number of payment periods for the loan or investment.
  - `pv` is the present value of the loan or investment (principal).
  - `start_period` is the first period in the range of payment periods for which to calculate the interest.
  - `end_period` is the last period in the range of payment periods for which to calculate the interest.
  - `type` specifies when payments are due:
    - `0` = End of the period.
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=CUMIPMT(5%/12, 60, 30000, 1, 12, 0)` calculates the total interest paid over the first year (12 months) on
    a 5% annual interest rate loan with 60 total payments and a principal of 30,000 (payments are made at the end of
    the period).
  - `=CUMIPMT(A1, A2, A3, A4, A5, A6)` calculates the cumulative interest using cell references for rate, number of
    periods, present value, start and end periods, and payment type.

### [CUMPRINC](./financial-functions/cum_princ.md)
Calculates the cumulative principal paid on a loan or an investment between two periods.

- **Purpose:** This function is essential for determining the total principal paid over a specified range of payment
  periods, which is particularly useful in financial analysis and loan management.

- **Formula:** `CUMPRINC(rate, nper, pv, start_period, end_period, type)`
  - `rate` is the annual interest rate of the loan or investment.
  - `nper` is the total number of payment periods for the loan or investment.
  - `pv` is the present value of the loan or investment (principal).
  - `start_period` is the first period in the range of payment periods for which to calculate the principal.
  - `end_period` is the last period in the range of payment periods for which to calculate the principal.
  - `type` specifies when payments are due:
    - `0` = End of the period.
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=CUMPRINC(5%/12, 60, 30000, 1, 12, 0)` calculates the total principal paid over the first year (12 months) on a 5%
    annual interest rate loan with 60 total payments and a principal of 30,000 (payments are made at the end of the
    period).
  - `=CUMPRINC(A1, A2, A3, A4, A5, A6)` computes the cumulative principal using cell references for rate, number of
    periods, present value, start and end periods, and payment type.

## D

### [DB](./financial-functions/db.md)
Calculates the depreciation of an asset for a specified period using the fixed-declining-balance method.

- **Purpose:** This function is used to determine the depreciation expense of an asset for a given period, based on the
  fixed-declining balance method, which is a common depreciation method in financial analysis.

- **Formula:** `DB(cost, salvage, life, period, [month])`
  - `cost` is the initial cost of the asset.
  - `salvage` is the salvage value of the asset (value at the end of the depreciation period).
  - `life` is the total number of periods (useful life) over which the asset will be depreciated.
  - `period` is the specific period for which to calculate depreciation.
  - `month` (optional) specifies the number of months in the first year of depreciation (defaults to 12 if omitted).

- **Example Usage:**
  - `=DB(10000, 1000, 5, 1)` calculates the depreciation for the first year for an asset with an initial cost of 10,000,
    a salvage value of 1,000, and a useful life of 5 years.
  - `=DB(A1, A2, A3, A4, A5)` computes the depreciation for the specified period using cell references for cost, salvage
    value, useful life, period, and number of months.

### [DDB](./financial-functions/ddb.md)
Calculates the depreciation of an asset for a specified period using the double-declining balance method.

- **Purpose:** This function is used to determine the depreciation expense of an asset for a given period, based on the
  double-declining balance method, which accelerates depreciation compared to the straight-line method.

- **Formula:** `DDB(cost, salvage, life, period, [factor])`
  - `cost` is the initial cost of the asset.
  - `salvage` is the salvage value of the asset (value at the end of the depreciation period).
  - `life` is the total number of periods (useful life) over which the asset will be depreciated.
  - `period` is the specific period for which to calculate depreciation.
  - `factor` (optional) specifies the rate of depreciation acceleration (defaults to 2 for double-declining balance).

- **Example Usage:**
  - `=DDB(10000, 1000, 5, 1)` calculates the depreciation for the first year for an asset with an initial cost of
    10,000, a salvage value of 1,000, and a useful life of 5 years, using the default factor of 2.
  - `=DDB(A1, A2, A3, A4, 1.5)` computes the depreciation for the specified period using cell references for cost,
    salvage value, useful life, period, and a custom factor of 1.5.

### [DISC](./financial-functions/disc.md)
Calculates the discount rate for a security.

- **Purpose:** This function is essential for determining the discount rate of a security based on its price, redemption
  value, and duration.

- **Formula:** `DISC(settlement, maturity, pr, redemption, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `pr` is the price of the security per $100 face value.
  - `redemption` is the redemption value of the security per $100 face value.
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=DISC(DATE(2023,1,15), DATE(2024,1,15), 95, 100)` calculates the discount rate for a security with a settlement
    date of January 15, 2023, maturity one year later, a price of $95, and a redemption value of $100 using a default
    day-count basis.
  - `=DISC(A1, A2, A3, A4, 1)` computes the discount rate using cell references for settlement date, maturity date,
    price, redemption value, and an actual/actual day-count basis.

### [DOLLARDE](./financial-functions/dollar_de.md)
Converts a dollar price expressed as a fraction into a decimal dollar value.

- **Purpose:** This function is used to convert a financial value expressed in fractional notation (such as bond prices)
  into its equivalent decimal form to simplify calculations and analysis.

- **Formula:** `DOLLARDE(fractional_dollar, fraction)`
  - `fractional_dollar` is the dollar value expressed as a fraction (e.g., `$1.75` where `0.75` represents fractional
    parts like `3/4`).
  - `fraction` is the denominator of the fraction used in the fractional dollar value (e.g., `4` for quarters).
    - **Note:** `fraction` must be an integer greater than 0; otherwise, the function returns an error.

- **Example Usage:**
  - `=DOLLARDE(1.75, 4)` converts `$1.75` (1 and 75/100 as fractional) with a denominator of `4` into its equivalent
    decimal form.
  - `=DOLLARDE(A1, A2)` converts the value of `A1` expressed as a fractional dollar into decimal using the denominator
    in `A2`.

### [DOLLARFR](./financial-functions/dollar_fr.md)
Converts a dollar price expressed as a decimal into a fraction dollar value.

- **Purpose:** This function is used to convert a financial value expressed in decimal form (e.g., bond prices) into its
  equivalent fractional form for easier representation in specific contexts, such as trading or reporting.

- **Formula:** `DOLLARFR(decimal_dollar, fraction)`
  - `decimal_dollar` is the dollar value expressed in decimal form (e.g., `$1.75`).
  - `fraction` is the denominator of the fraction used for the conversion (e.g., `4` for quarters).
    - **Note:** `fraction` must be an integer greater than 0; otherwise, the function returns an error.

- **Example Usage:**
  - `=DOLLARFR(1.75, 4)` converts `$1.75` (1 and 75/100 in decimal form) into its equivalent fractional form with a
    denominator of `4`: `$1.3` (`1 and 3/4`).
  - `=DOLLARFR(A1, A2)` converts the value in `A1` (expressed as a decimal) into its fractional equivalent using the
    denominator specified in `A2`.

### [DURATION](./financial-functions/duration.md)
Calculates the Macauley duration of a security with periodic interest payments.

- **Purpose:** This function is used to determine the Macauley duration of a security, which is a measure of the
  weighted average time until a security's cash flows are received. It is commonly used in bond pricing and interest
  rate risk management.

- **Formula:** `DURATION(settlement, maturity, coupon, yld, frequency, [basis])`
  - `settlement` is the settlement date of the security.
  - `maturity` is the maturity date of the security.
  - `coupon` is the annual coupon rate of the security.
  - `yld` is the annual yield of the security.
  - `frequency` specifies the number of coupon payments per year:
    - `1` = Annual.
    - `2` = Semi-annual.
    - `4` = Quarterly.
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=DURATION(DATE(2023,1,1), DATE(2033,1,1), 5%, 4%, 2)` calculates the Macauley duration of a 10-year bond with a 5%
    annual coupon rate, 4% annual yield, and semi-annual coupon payments using the default 30/360 day-count basis.
  - `=DURATION(A1, A2, A3, A4, A5, 1)` computes the Macauley duration using cell references for settlement date,
    maturity date, coupon rate, annual yield, frequency, and an actual/actual day-count basis.

## E

### [EFFECT](./financial-functions/effect.md)
Calculates the effective annual interest rate based on the nominal annual interest rate and the number of compounding
periods per year.

- **Purpose:** This function is used to determine the effective annual interest rate, which accounts for the effects of
  compounding over a year, making it easier to compare rates across financial products with different compounding
  frequencies.

- **Formula:** `EFFECT(nominal_rate, npery)`
  - `nominal_rate` is the nominal (stated) annual interest rate.
  - `npery` is the number of compounding periods per year.

- **Example Usage:**
  - `=EFFECT(5%, 4)` calculates the effective annual interest rate for a nominal rate of 5% with quarterly compounding (
    4 periods per year).
  - `=EFFECT(A1, A2)` computes the effective interest rate using the nominal annual rate in `A1` and the number of
    compounding periods in `A2`.

- **Notes:**
  - `nominal_rate` must be greater than 0.
  - `npery` must be an integer greater than or equal to 1; otherwise, the function returns an error.

## F

### [FV](./financial-functions/fv.md)
Calculates the future value of an investment based on periodic, constant payments and a constant interest rate.

- **Purpose:** This function is used to determine the future value of an investment or loan when you know the periodic
  payments, interest rate, and duration.

- **Formula:** `FV(rate, nper, pmt, [pv], [type])`
  - `rate` is the interest rate per period.
  - `nper` is the total number of periods.
  - `pmt` is the payment made each period (negative for outgoing payments).
  - `pv` (optional) is the present value or initial investment. Default is `0`.
  - `type` (optional) indicates when payments are due:
    - `0` = End of the period (default).
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=FV(5%/12, 60, -100, -1000)` calculates the future value of an investment with monthly payments
    of $100, an initial investment of $1000, over 60 months at an annual interest rate of 5% (monthly rate = `5%/12`).
  - `=FV(A1, A2, A3, A4, 1)` computes the future value using cell references for rate, number of periods, payments,
    initial present value, and assumes payments are made at the beginning of the period.

### [FVSCHEDULE](./financial-functions/fv_schedule.md)
Calculates the future value of an investment based on a starting principal and a schedule of interest rates.

- **Purpose:** This function is used to determine how much an investment will grow based on a series of varying interest
  rates over time.

- **Formula:** `FVSCHEDULE(principal, schedule)`
  - `principal` is the initial amount of the investment.
  - `schedule` is an array (or range) of interest rates applied to the investment for each period.

- **Example Usage:**
  - `=FVSCHEDULE(1000, {0.05, 0.04, 0.03})` calculates the future value of a $1000 investment after applying 5%, 4%, and
    3% interest rates over three periods.
  - `=FVSCHEDULE(A1, A2:A4)` computes the future value using the principal in `A1` and the schedule of interest rates in
    the range `A2:A4`.

- **Notes:**
  - The `schedule` array can contain positive, negative, or zero values, representing various interest rate scenarios.
  - If the `schedule` array is empty, the function returns the initial `principal`.

## I

### [INTRATE](./financial-functions/int_rate.md)
Calculates the interest rate for a fully invested security.

- **Purpose:** This function determines the annual interest rate for a security given its settlement and maturity dates,
  investment amount, and redemption value.

- **Formula:** `INTRATE(settlement, maturity, investment, redemption, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the security (the date when the security expires).
  - `investment` is the amount invested in the security.
  - `redemption` is the amount to be received at maturity.
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=INTRATE(DATE(2022,1,1), DATE(2023,1,1), 1000, 1050)` calculates the annual interest rate for an investment
    of $1000 with a redemption value of $1050 and a one-year term using the default 30/360 day-count basis.
  - `=INTRATE(A1, A2, A3, A4, 1)` computes the interest rate based on the settlement date, maturity date, investment,
    redemption, and an actual/actual day-count basis specified in the referenced cells.

### [IPMT](./financial-functions/i_pmt.md)
Calculates the interest portion of a payment for a given period in an investment or loan with constant periodic payments
and a constant interest rate.

- **Purpose:** This function is used to determine the interest component of a payment during a specific period. It is
  useful for understanding how much of each payment is applied toward interest.

- **Formula:** `IPMT(rate, per, nper, pv, [fv], [type])`
  - `rate` is the interest rate per period.
  - `per` is the period for which the interest component is calculated (must be between `1` and `nper`).
  - `nper` is the total number of periods.
  - `pv` is the present value or principal of the loan/investment.
  - `fv` (optional) is the future value or the desired balance after the last payment. Default is `0`.
  - `type` (optional) indicates when payments are due:
    - `0` = End of the period (default).
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=IPMT(5%/12, 1, 60, -10000)` calculates the interest portion of the first monthly payment for a 5-year loan of $
    10,000 with a 5% annual interest rate compounded monthly.
  - `=IPMT(A1, A2, A3, A4, 0, 1)` computes the interest portion using cell references for rate, period, total periods,
    loan value, a future value of `0`, and payments due at the beginning of the period.

### [IRR](./financial-functions/irr.md)
Calculates the internal rate of return for a series of cash flows occurring at regular intervals.

- **Purpose:** This function is used to determine the discount rate at which the net present value (NPV) of a series of
  cash flows equals zero. It’s widely used in financial analysis to evaluate the profitability of investments.

- **Formula:** `IRR(values, [guess])`
  - `values` is an array (or range) of cash flows, where:
    - The first value represents the initial investment (typically negative).
    - Subsequent values represent net cash inflows or outflows occurring at regular intervals.
  - `guess` (optional) is a number that serves as a starting point for the iterative calculation. Default is `0.1` (
    10%).

- **Example Usage:**
  - `=IRR({-1000, 200, 300, 400, 500})` calculates the internal rate of return for an investment with an initial cost
    of $1000 and cash inflows of $200, $300, $400, and $500 over four periods.
  - `=IRR(A1:A5, 0.1)` computes the IRR using the cash flows in the range `A1:A5` and a guess of `10%`.

### [ISPMT](./financial-functions/is_pmt.md)
Calculates the interest paid during a specific period of an investment or loan amortized over time.

- **Purpose:** This function is used to determine the interest paid on the principal for a specific period assuming
  arithmetic (linear) amortization.

- **Formula:** `ISPMT(rate, per, nper, pv)`
  - `rate` is the interest rate per period.
  - `per` is the specific period for which the interest is calculated (must be between `1` and `nper`).
  - `nper` is the total number of periods.
  - `pv` is the present value or principal of the loan/investment.

- **Example Usage:**
  - `=ISPMT(5%/12, 1, 60, -10000)` calculates the interest for the first period of a 5-year loan of $10,000 with a 5%
    annual interest rate compounded monthly.
  - `=ISPMT(A1, A2, A3, A4)` computes the interest based on the interest rate, period, total periods, and loan value
    provided in cells `A1`, `A2`, `A3`, and `A4`.

## M

### [MDURATION](./financial-functions/m_duration.md)
Calculates the modified duration of a security with periodic interest payments, which measures the price sensitivity of
the security to interest rate changes.

- **Purpose:** This function is used to determine the effective duration of a bond, considering the interest rate and
  coupon payments. It gives insight into the bond's interest rate risk.

- **Formula:** `MDURATION(settlement, maturity, coupon, yld, frequency, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the security (the date when the security expires).
  - `coupon` is the annual coupon rate of the security (as a percentage of face value).
  - `yld` is the annual yield of the security.
  - `frequency` is the number of coupon payments per year:
    - `1` = Annual
    - `2` = Semi-annual
    - `4` = Quarterly
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=MDURATION(DATE(2022, 1, 1), DATE(2032, 1, 1), 0.05, 0.06, 2)` calculates the modified duration of a bond with a 5%
    annual coupon rate, 6% annual yield, semi-annual payments, and a 10-year maturity.
  - `=MDURATION(A1, A2, A3, A4, A5, 0)` computes the modified duration using the settlement date, maturity date, coupon
    rate, annual yield, frequency, and a 30/360 day-count basis provided in the referenced cells.

### [MIRR](./financial-functions/m_irr.md)
Calculates the modified internal rate of return for a series of cash flows, considering both the cost of investment and
the reinvestment rate of returns.

- **Purpose:** This function is used to determine the profitability of an investment by taking into account both the
  financing cost and the reinvestment rate. MIRR adjusts the IRR by considering a more realistic reinvestment scenario.

- **Formula:** `MIRR(values, finance_rate, reinvest_rate)`
  - `values` is an array (or range) of cash flows, where:
    - The first value represents the initial investment (typically negative).
    - Subsequent values represent net cash inflows or outflows occurring at regular intervals.
  - `finance_rate` is the cost of financing or the rate at which the investment is financed.
  - `reinvest_rate` is the rate at which the positive cash flows are reinvested.

- **Example Usage:**
  - `=MIRR({-1000, 200, 300, 400, 500}, 0.1, 0.12)` calculates the modified internal rate of return for an investment
    with an initial cost of $1000, cash inflows of $200, $300, $400, and $500, a finance rate of 10%, and a reinvestment
    rate of 12%.
  - `=MIRR(A1:A5, 0.08, 0.1)` computes the MIRR using the cash flows in the range `A1:A5`, a financing rate of 8%, and
    a reinvestment rate of 10%.

## N

### [NOMINAL](./financial-functions/nominal.md)
Calculates the nominal annual interest rate given the effective annual rate and the number of compounding periods per
year.

- **Purpose:** This function is used to determine the nominal interest rate required to achieve a given effective
  interest rate over a specified number of compounding periods. It is commonly used in financial calculations to convert
  effective rates into nominal rates.

- **Formula:** `NOMINAL(effect_rate, npery)`
  - `effect_rate` is the effective annual interest rate (in decimal form, e.g., `0.05` for 5%).
  - `npery` is the number of compounding periods per year.

- **Example Usage:**
  - `=NOMINAL(0.05, 12)` calculates the nominal annual interest rate for an effective annual rate of 5% with monthly (
    12) compounding.
  - `=NOMINAL(A1, A2)` computes the nominal rate using the effective annual rate and the number of compounding periods
    specified in cells `A1` and `A2`.

### [NPER](./financial-functions/n_per.md)
Calculates the number of periods for an investment or loan based on constant periodic payments and a constant interest
rate.

- **Purpose:** This function is used to determine how many periods it will take to pay off a loan or reach an investment
  goal given periodic payments, an interest rate, and a future value.

- **Formula:** `NPER(rate, pmt, pv, [fv], [type])`
  - `rate` is the interest rate per period.
  - `pmt` is the payment made each period (must remain constant throughout the duration).
  - `pv` is the present value or the lump sum amount of the loan/investment.
  - `fv` (optional) is the future value or the desired value after the last payment. Default is `0`.
  - `type` (optional) indicates when payments are due:
    - `0` = End of the period (default).
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=NPER(5%/12, -200, -10000)` calculates the number of months required to pay off
    a $10,000 loan with a monthly payment of $200 and a 5% annual interest rate compounded monthly.
  - `=NPER(A1, A2, A3, 0, 1)` computes the number of periods using the interest rate, payment amount, present value, a
    future value of `0`, and payments due at the beginning of the period specified in cells `A1`, `A2`, and `A3`.

### [NPV](./financial-functions/npv.md)
Calculates the net present value of an investment based on a series of periodic cash flows and a discount rate.

- **Purpose:** This function is used to determine the present value of future cash flows based on a given discount rate,
  accounting for the time value of money.

- **Formula:** `NPV(rate, values)`
  - `rate` is the discount rate per period.
  - `values` is an array (or range) of cash flows, which can include both negative (outflows) and positive (inflows)
    values. Cash flows must be spaced equally in time.

- **Example Usage:**
  - `=NPV(0.08, {-1000, 300, 400, 500, 600})` calculates the net present value of an investment with an initial cost of
    $1000 (outflow), and cash inflows of $300, $400, $500, and $600 over four periods, using a discount rate of 8%.
  - `=NPV(A1, A2:A6)` calculates the NPV using the discount rate provided in cell `A1` and the cash flow values in the
    range `A2:A6`.

## O

### [ODDFPRICE](./financial-functions/odd_f_price.md)
Calculates the price per $100 face value of a security with an odd first period (longer or shorter than usual).

- **Purpose:** This function is used to determine the price of a bond with an irregular first coupon period. This is
  typically the result of bonds issued between standard coupon dates.

- **Formula:** `ODDFPRICE(settlement, maturity, issue, first_coupon, rate, yld, redemption, frequency, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the bond (the date when the bond expires).
  - `issue` is the issue date of the security (when the bond is issued).
  - `first_coupon` is the date of the first coupon payment.
  - `rate` is the annual coupon rate of the security (as a percentage of face value).
  - `yld` is the annual yield of the security (the interest rate of the bond).
  - `redemption` is the redemption value of the bond per $100 of face value.
  - `frequency` is the number of coupon payments per year:
    - `1` = Annual
    - `2` = Semi-annual
    - `4` = Quarterly
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=ODDFPRICE(DATE(2023, 1, 15), DATE(2030, 1, 15), DATE(2022, 7, 1), DATE(2023, 3, 1), 0.04, 0.05, 100, 2)`
    calculates the price of a bond with a 4% annual coupon rate, a 5% annual yield, a semi-annual payment frequency, a
    maturity date of January 15, 2030, and an odd first coupon period ending on March 1, 2023.
  - `=ODDFPRICE(A1, A2, A3, A4, A5, A6, 100, A7, 1)` computes the price of a bond with the settlement date, maturity
    date, issue date, first coupon date, coupon rate, yield, redemption value, frequency, and day-count basis provided
    in the referenced cells.

### [ODDFYIELD](./financial-functions/odd_f_yield.md)
Calculates the yield of a security with an odd first period (longer or shorter than usual).

- **Purpose:** This function is used to determine the yield of a bond with an irregular first coupon period, often
  observed in bonds issued between standard coupon dates.

- **Formula:** `ODDFYIELD(settlement, maturity, issue, first_coupon, rate, price, redemption, frequency, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the bond (the date when the bond expires).
  - `issue` is the issue date of the security (when the bond is issued).
  - `first_coupon` is the date of the first coupon payment.
  - `rate` is the annual coupon rate of the security (as a percentage of face value).
  - `price` is the price of the security per $100 of face value.
  - `redemption` is the redemption value of the bond per $100 of face value.
  - `frequency` is the number of coupon payments per year:
    - `1` = Annual
    - `2` = Semi-annual
    - `4` = Quarterly
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=ODDFYIELD(DATE(2023, 1, 15), DATE(2030, 1, 15), DATE(2022, 7, 1), DATE(2023, 3, 1), 0.04, 95, 100, 2)`
    calculates the yield of a bond with a 4% annual coupon rate, a price of $95 per $100 face value, a semi-annual
    payment frequency, a maturity date of January 15, 2030, and an odd first coupon period ending on March 1, 2023.
  - `=ODDFYIELD(A1, A2, A3, A4, A5, A6, 100, A7, 1)`
    computes the yield of a bond using the settlement date, maturity date, issue date, first coupon date, coupon rate,
    bond price, redemption value, frequency, and day-count basis provided in the referenced cells.

### [ODDLPRICE](./financial-functions/odd_l_price.md)
Calculates the price of a security with an odd last period (longer or shorter than usual).

- **Purpose:** This function is used to determine the price of a bond with an irregular last coupon period, often
  observed in bonds maturing between standard coupon dates.

- **Formula:** `ODDLPRICE(settlement, maturity, last_coupon, rate, yld, redemption, frequency, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the bond (the date when the bond expires).
  - `last_coupon` is the date of the last coupon payment before maturity.
  - `rate` is the annual coupon rate of the security (as a percentage of face value).
  - `yld` is the annual yield of the security (the interest rate of the bond).
  - `redemption` is the redemption value of the bond per $100 of face value.
  - `frequency` is the number of coupon payments per year:
    - `1` = Annual
    - `2` = Semi-annual
    - `4` = Quarterly
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=ODDLPRICE(DATE(2023, 1, 15), DATE(2030, 1, 15), DATE(2029, 7, 1), 0.04, 0.05, 100, 2)`
    calculates the price of a bond with a 4% annual coupon rate, a 5% annual yield, a semi-annual payment frequency, a
    maturity date of January 15, 2030, and an odd last coupon period starting on July 1, 2029.
  - `=ODDLPRICE(A1, A2, A3, A4, A5, 100, A6, 1)` computes the price of a bond using the settlement date, maturity date,
    last coupon date, coupon rate, yield, redemption value, frequency, and day-count basis provided in the referenced
    cells.

### [ODDLYIELD](./financial-functions/odd_l_yield.md)
Calculates the yield of a security with an odd last period (longer or shorter than usual).

- **Purpose:** This function is used to determine the yield of a bond with an irregular last coupon period, often
  observed in bonds maturing between standard coupon dates.

- **Formula:** `ODDLYIELD(settlement, maturity, last_coupon, rate, price, redemption, frequency, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the bond (the date when the bond expires).
  - `last_coupon` is the date of the last coupon payment before maturity.
  - `rate` is the annual coupon rate of the security (as a percentage of face value).
  - `price` is the price of the security per $100 of face value.
  - `redemption` is the redemption value of the bond per $100 of face value.
  - `frequency` is the number of coupon payments per year:
    - `1` = Annual
    - `2` = Semi-annual
    - `4` = Quarterly
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=ODDLYIELD(DATE(2023, 1, 15), DATE(2030, 1, 15), DATE(2029, 7, 1), 0.04, 95, 100, 2)`  
    calculates the yield of a bond with a 4% annual coupon rate, a price of $95 per $100 face value, a semi-annual
    payment frequency, a maturity date of January 15, 2030, and an odd last coupon period starting on July 1, 2029.
  - `=ODDLYIELD(A1, A2, A3, A4, A5, 100, A6, 1)`  
    computes the yield of a bond using the settlement date, maturity date, last coupon date, coupon rate, bond price,
    redemption value, frequency, and day-count basis provided in the referenced cells.

## P

### [PDURATION](./financial-functions/p_duration.md)
Calculates the number of periods required for an investment to grow to a specified future value given a fixed interest
rate.

- **Purpose:** This function is used to determine how long it will take for a given investment to grow to a specified
  future value, assuming a fixed periodic interest rate.

- **Formula:** `PDURATION(rate, pv, fv)`
  - `rate` is the interest rate per period (must be positive).
  - `pv` is the present value or initial amount of the investment.
  - `fv` is the future value or the amount to which the investment is expected to grow.

- **Example Usage:**
  - `=PDURATION(0.05, 1000, 2000)` calculates the number of periods required for a $1000 investment to grow to $2000
    with a 5% rate of return per period.
  - `=PDURATION(A1, A2, A3)` computes the number of periods using the rate in `A1`, present value in `A2`, and desired
    future value in `A3`.

### [PMT](./financial-functions/pmt.md)
Calculates the payment for a loan based on constant payments and a constant interest rate.

- **Purpose:** This function is used to calculate the payment amount for a loan or investment based on a fixed interest
  rate and a fixed number of periods.

- **Formula:** `PMT(rate, nper, pv, [fv], [type])`
  - `rate` is the interest rate per period.
  - `nper` is the total number of payment periods in the loan or investment.
  - `pv` is the present value or total loan amount.
  - `fv` (optional) is the future value or the remaining balance after the final payment (default is 0).
  - `type` (optional) indicates when payments are due:
    - `0` = End of the period (default if omitted).
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=PMT(0.05/12, 60, -30000)` calculates the monthly payment for a loan of $30,000 over 5 years with an annual
    interest rate of 5%. Payments are made at the end of the period, and there is no remaining balance.
  - `=PMT(A1/12, A2, A3)` computes the payment amount using the interest rate in `A1`, the number of periods in `A2`,
    and the loan amount in `A3`.

### [PPMT](./financial-functions/p_pmt.md)
Calculates the payment on the principal for a loan or investment based on constant payments and a constant interest rate
for a given period.

- **Purpose:** This function is used to calculate the principal portion of a payment for a specific period in the
  lifetime of a loan or investment, assuming fixed periodic payments and a constant interest rate.

- **Formula:** `PPMT(rate, per, nper, pv, [fv], [type])`
  - `rate` is the interest rate per period.
  - `per` is the specific period for which you want to calculate the principal payment (must be between 1 and `nper`).
  - `nper` is the total number of payment periods in the loan or investment.
  - `pv` is the present value or total loan amount.
  - `fv` (optional) is the future value or the remaining balance after the final payment (default is 0).
  - `type` (optional) indicates when payments are due:
    - `0` = End of the period (default if omitted).
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=PPMT(0.05/12, 1, 60, -30000)` calculates the principal portion of the first monthly payment for a $30,000 loan
    with a 5% annual interest rate over 5 years. Payments are made at the end of the month, and there is no remaining
    balance.
  - `=PPMT(A1/12, A2, A3, A4)` computes the principal portion of a payment using the interest rate in `A1`, the period
    in `A2`, the number of periods in `A3`, and the loan amount in `A4`.

### [PRICE](./financial-functions/price.md)
Calculates the price per $100 face value of a security that pays periodic interest.

- **Purpose:** This function is used to determine the market price of a bond or similar security paying periodic
  interest based on a constant yield.

- **Formula:** `PRICE(settlement, maturity, rate, yield, redemption, frequency, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the security (the date when the security expires).
  - `rate` is the annual coupon rate of the security (as a percentage of face value).
  - `yield` is the annual yield of the security (as a percentage of face value).
  - `redemption` is the redemption value of the bond per $100 of face value.
  - `frequency` is the number of coupon payments per year:
    - `1` = Annual
    - `2` = Semi-annual
    - `4` = Quarterly
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=PRICE(DATE(2023, 1, 15), DATE(2030, 1, 15), 0.04, 0.05, 100, 2)` calculates the price of a bond with a 4% annual
    coupon rate, a 5% annual yield, a semi-annual payment frequency, a maturity date of January 15, 2030, and assumes
    the default day-count basis of 30/360.
  - `=PRICE(A1, A2, A3, A4, 100, A5, 1)` computes the price of a bond using the settlement date, maturity date,
    coupon rate, yield, redemption value, payment frequency, and day-count basis specified in referenced cells.

### [PRICEDISC](./financial-functions/price_disc.md)
Calculates the price per $100 face value of a discounted security.

- **Purpose:** This function is used to calculate the price of a discounted security (such as a Treasury bill) based on
  its face value, discount rate, and time to maturity.

- **Formula:** `PRICEDISC(settlement, maturity, discount, [redemption], [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the security (the date when the security expires).
  - `discount` is the discount rate of the security (as a percentage of face value).
  - `redemption` is the redemption value of the security per $100 of face value (default is $100).
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=PRICEDISC(DATE(2023, 1, 1), DATE(2024, 1, 1), 0.05)` calculates the price of a discounted security with a 5%
    discount rate, a maturity date of January 1, 2024, and assumes the default redemption value of $100 and the 30/360
    day-count basis.
  - `=PRICEDISC(A1, A2, A3, A4, A5)` computes the price of a discounted security using the settlement date in `A1`,
    maturity date in `A2`, discount rate in `A3`, redemption value in `A4`, and day-count basis in `A5`.

### [PRICEMAT](./financial-functions/price_mat.md)
Calculates the price per $100 face value of a security that pays interest at maturity.

- **Purpose:** This function is used to determine the market price of a security that pays interest at maturity, based
  on
  the settlement date, maturity date, annual coupon rate, yield, and day-count basis.

- **Formula:** `PRICEMAT(settlement, maturity, issue, rate, yield, [basis])`
  - `settlement` is the settlement date of the security (the date after issuance when the security is purchased).
  - `maturity` is the maturity date of the security (the date when the security expires).
  - `issue` is the issue date of the security (the original date the security was issued).
  - `rate` is the annual coupon rate of the security (as a percentage of face value).
  - `yield` is the annual yield of the security (as a percentage of face value).
  - `basis` (optional) specifies the day-count basis to use:
    - `0` = 30/360 (US convention, default if omitted).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

- **Example Usage:**
  - `=PRICEMAT(DATE(2023, 1, 15), DATE(2030, 1, 15), DATE(2022, 1, 15), 0.04, 0.05)` calculates the price of a security
    with a 4% annual coupon rate, 5% annual yield, issue date of January 15, 2022, and maturity date of January 15,
    2030,
    assuming the default day-count basis of 30/360.
  - `=PRICEMAT(A1, A2, A3, A4, A5, A6)` computes the price of a security using the settlement date in `A1`, maturity
    date
    in `A2`, issue date in `A3`, coupon rate in `A4`, yield in `A5`, and day-count basis in `A6`.


### [PV](./financial-functions/pv.md)
Calculates the present value of a loan or investment based on a constant periodic interest rate and number of payment
periods.

- **Purpose:** This function is used to determine the current value of a series of future payments or receipts, given a
  fixed periodic interest rate.

- **Formula:** `PV(rate, nper, pmt, [fv], [type])`
  - `rate` is the interest rate per period.
  - `nper` is the total number of payment periods.
  - `pmt` is the payment made each period (must be consistent throughout).
  - `fv` (optional) is the future value or cash balance desired after the last payment (default is 0).
  - `type` (optional) indicates when payments are due:
    - `0` = End of the period (default if omitted).
    - `1` = Beginning of the period.

- **Example Usage:**
  - `=PV(0.05/12, 60, -500)` calculates the present value of a loan with monthly payments of $500 over 5 years at a 5%
    annual interest rate. Payments are made at the end of each period, and there is no remaining balance.
  - `=PV(A1/12, A2, A3, A4, A5)` computes the present value using the interest rate in `A1`, the number of periods in
    `A2`, the payment in `A3`, the future value in `A4`, and the payment type in `A5`.

## R

### [RATE](./financial-functions/rate.md)
Calculates the interest rate per period of a loan or investment.

- **Purpose:** This function is used to determine the periodic interest rate required for an investment or loan to
  achieve a specified future value, given periodic payments, a present value, and the number of periods.

- **Formula:** `RATE(nper, pmt, pv, [fv], [type], [guess])`
  - `nper` is the total number of payment periods in the investment or loan.
  - `pmt` is the payment made each period (must be consistent throughout).
  - `pv` is the present value or starting amount of the investment or loan.
  - `fv` (optional) is the future value or desired balance after the last payment (default is 0).
  - `type` (optional) indicates when payments are due:
    - `0` = End of the period (default if omitted).
    - `1` = Beginning of the period.
  - `guess` (optional) is your guess for the rate (default is 0.1 or 10%).

- **Example Usage:**
  - `=RATE(60, -500, 20000)` calculates the periodic interest rate for a loan of $20,000 with monthly payments of $500
    over 60 months, assuming payments are made at the end of each period.
  - `=RATE(A1, A2, A3, A4, A5, A6)` computes the periodic interest rate using the total number of periods in `A1`, the
    periodic payment amount in `A2`, the present value in `A3`, the future value in `A4`, the payment type in `A5`, and
    the initial rate guess in `A6`.

### [RECEIVED](./financial-functions/received.md)
Calculates the amount received at maturity for a fully invested security.

- **Purpose:** This function is used to calculate the amount received at maturity for a security that is purchased at a
  discount to its face value, given the settlement date, maturity date, discount rate, and security's face value.

- **Formula:** `RECEIVED(settlement, maturity, discount, [redemption], [basis])`
  - **settlement**: The date when the security is purchased or settled. This is the **start date** of the investment.
  - **maturity**: The date when the security matures and the investor receives the payment. This must be after the
    settlement date.
  - **investment**: The amount invested or the initial price paid for the security.
  - **discount**: The annual discount rate of the security (as a decimal or percentage).
  - **[basis]** *(optional)*: The day count basis used to calculate the interest. Defaults to `0` (US 30/360 convention)
    if omitted. Possible values:
    - `0`: US (NASD) 30/360.
    - `1`: Actual/actual.
    - `2`: Actual/360.
    - `3`: Actual/365.
    - `4`: European 30/360.

- **Example Usage:**
  - `=RECEIVED(DATE(2023, 1, 15), DATE(2025, 1, 15), 0.05)` calculates the amount received at maturity for a security
    purchased on January 15, 2023, with a maturity date of January 15, 2025, and an annual discount rate of 5%, assuming
    a redemption value of $100 and the default day-count basis of 30/360.
  - `=RECEIVED(A1, A2, A3, A4, A5)` computes the maturity amount using the settlement date in `A1`, the maturity date in
    `A2`, the discount rate in `A3`, the redemption value in `A4`, and the day-count basis in `A5`.

### [RRI](./financial-functions/rri.md)
Calculates the equivalent interest rate for the growth of an investment.

- **Purpose:** This function is used to determine the equivalent annual growth rate of an investment over a specified
  number of periods.

- **Formula:** `RRI(nper, pv, fv)`
  - `nper` is the number of periods during which the investment grows.
  - `pv` is the present value or the starting amount of the investment.
  - `fv` is the future value or the end amount of the investment.

- **Example Usage:**
  - `=RRI(10, 1000, 2000)` calculates the annual growth rate required for an investment to grow from $1,000 to $2,000
    over 10 years.
  - `=RRI(A1, A2, A3)` computes the equivalent growth rate using the number of periods in `A1`, the starting value in
    `A2`, and the ending value in `A3`.

## S

### [SLN](./financial-functions/sln.md)
Calculates the straight-line depreciation of an asset for one period.

- **Purpose:** This function is used to compute the depreciation of an asset at a constant rate over its useful life.

- **Formula:** `SLN(cost, salvage, life)`
  - `cost`: The initial cost or purchase price of the asset.
  - `salvage`: The value of the asset at the end of its useful life.
  - `life`: The total useful life of the asset (in periods).

- **Example Usage:**
  - `=SLN(5000, 200, 10)` calculates the annual depreciation of an asset with an initial cost
    of $5,000, a salvage value of $200, and a useful life of 10 years.
  - `=SLN(A1, A2, A3)` computes the straight-line depreciation using the cost in `A1`, the salvage value in `A2`, and
    the asset's useful life in `A3`.

### [SYD](./financial-functions/syd.md)
Calculates the sum-of-years' digits depreciation of an asset for a specified period.

- **Purpose:** This function is used to compute the depreciation of an asset at an accelerated rate over its useful life
  based on the sum-of-years' digits method.

- **Formula:** `SYD(cost, salvage, life, period)`
  - `cost`: The initial cost or purchase price of the asset.
  - `salvage`: The value of the asset at the end of its useful life.
  - `life`: The total useful life of the asset (in periods).
  - `period`: The specific period for which depreciation is calculated (must be between 1 and `life`).

- **Example Usage:**
  - `=SYD(5000, 200, 10, 1)` calculates the depreciation for the first year of an asset with an initial cost
    of $5,000, a salvage value of $200, and a useful life of 10 years.
  - `=SYD(A1, A2, A3, A4)` computes the sum-of-years' digits depreciation using the cost in `A1`, the salvage value in
    `A2`, the asset's useful life in `A3`, and the period in `A4`.

## T

### [TBILLEQ](./financial-functions/t_bill_eq.md)
Calculates the bond-equivalent yield for a Treasury bill.

- **Purpose:** This function is used to compute the annualized yield of a Treasury bill based on its discount rate.

- **Formula:** `TBILLEQ(settlement, maturity, discount)`
  - `settlement`: The date when the Treasury bill is purchased or settled. This is the **start date** of the investment.
  - `maturity`: The date when the Treasury bill matures.
  - `discount`: The discount rate of the Treasury bill (as a decimal or percentage).

- **Example Usage:**
  - `=TBILLEQ(DATE(2023, 1, 15), DATE(2023, 7, 15), 0.045)` calculates the bond-equivalent yield for a Treasury bill
    purchased on January 15, 2023, with a maturity date of July 15, 2023, and a 4.5% discount rate.
  - `=TBILLEQ(A1, A2, A3)` computes the bond-equivalent yield using the settlement date in `A1`, the maturity date in
    `A2`, and the discount rate in `A3`.

### [TBILLPRICE](./financial-functions/t_bill_price.md)
Calculates the price per $100 face value for a Treasury bill.

- **Purpose:** This function is used to compute the price of a Treasury bill based on the settlement date, maturity
  date, and the discount rate.

- **Formula:** `TBILLPRICE(settlement, maturity, discount)`
  - `settlement`: The date when the Treasury bill is purchased or settled. This is the **start date** of the investment.
  - `maturity`: The date when the Treasury bill matures.
  - `discount`: The discount rate of the Treasury bill (as a decimal or percentage).

- **Example Usage:**
  - `=TBILLPRICE(DATE(2023, 1, 15), DATE(2023, 7, 15), 0.045)` calculates the price of a Treasury bill with a settlement
    date of January 15, 2023, a maturity date of July 15, 2023, and a 4.5% discount rate.
  - `=TBILLPRICE(A1, A2, A3)` computes the price using the settlement date in `A1`, the maturity date in `A2`, and the
    discount rate in `A3`.

### [TBILLYIELD](./financial-functions/t_bill_yield.md)
Calculates the yield of a Treasury bill.

- **Purpose:** This function is used to compute the annualized yield of a Treasury bill based on its settlement date,
  maturity date, and price.

- **Formula:** `TBILLYIELD(settlement, maturity, price)`
  - `settlement`: The date when the Treasury bill is purchased or settled. This is the **start date** of the investment.
  - `maturity`: The date when the Treasury bill matures.
  - `price`: The price per $100 face value of the Treasury bill.

- **Example Usage:**
  - `=TBILLYIELD(DATE(2023, 1, 15), DATE(2023, 7, 15), 98.5)` calculates the annualized yield for a Treasury bill
    purchased on January 15, 2023, with a maturity date of July 15, 2023, and a price of $98.50 per $100 face value.
  - `=TBILLYIELD(A1, A2, A3)` computes the yield using the settlement date in `A1`, the maturity date in `A2`, and
    the price in `A3`.

## V

### [VDB](./financial-functions/vdb.md)
Calculates the depreciation of an asset for a specified period using the variable declining balance method.

- **Purpose:** This function is used to compute the depreciation of an asset at an accelerated rate over multiple
  periods, where the depreciation rate can vary.

- **Formula:** `VDB(cost, salvage, life, start_period, end_period, [factor], [no_switch])`
  - `cost`: The initial cost or purchase price of the asset.
  - `salvage`: The value of the asset at the end of its useful life.
  - `life`: The total useful life of the asset (in periods).
  - `start_period`: The start of the period for which depreciation is calculated.
  - `end_period`: The end of the period for which depreciation is calculated.
  - `factor` (optional): The rate at which the balance declines. If omitted, defaults to 2 (for double-declining
    balance).
  - `no_switch` (optional): A logical value indicating whether to switch to straight-line depreciation when it is more
    advantageous. Defaults to `FALSE`.

- **Example Usage:**
  - `=VDB(10000, 2000, 5, 0, 1)` calculates the depreciation for the first year of an asset with an initial cost
    of $10,000, a salvage value of $2,000, and a useful life of 5 years.
  - `=VDB(10000, 2000, 5, 1, 3, 1.5, TRUE)` computes the depreciation from year 1 to year 3 using a factor of 1.5 and
    without switching to straight-line depreciation.
  - `=VDB(A1, A2, A3, A4, A5, A6, A7)` computes the variable declining balance depreciation using values from cells `A1`
    through `A7`.

## X

### [XIRR](./financial-functions/x_irr.md)
Calculates the internal rate of return for a series of cash flows occurring at irregular intervals.

- **Purpose:** This function is used to compute the internal rate of return (IRR) for a schedule of cash flows that are
  not equally spaced in time.

- **Formula:** `XIRR(cashflows, dates, [guess])`
  - `cashflows`: An array of cash flow amounts. These can be positive (inflows) and negative (outflows).
  - `dates`: An array of dates corresponding to the cash flows. The first date in the array is considered the start of
    the schedule.
  - `guess` (optional): An optional value for the initial guess of the IRR. Defaults to 0.10 (10%) if omitted.

- **Example Usage:**
  - `=XIRR({-10000, 2750, 4250, 3250, 2750}, {DATE(2023, 1, 1), DATE(2023, 6, 1), DATE(2024, 1, 1), DATE(2024, 6, 1), DATE(2025, 1, 1)})`
  calculates the internal rate of return for a series of cash flows and their associated dates.
  - `=XIRR(A1:A5, B1:B5, 0.1)` computes the IRR using cash flow data from `A1:A5`, corresponding dates from `B1:B5`, and
    an initial guess of 10%.

### [XNPV](./financial-functions/x_npv.md)
Calculates the net present value for a series of cash flows occurring at irregular intervals.

- **Purpose:** This function is used to compute the net present value (NPV) for a schedule of cash flows that are
  not equally spaced in time, using a specified discount rate.

- **Formula:** `XNPV(rate, cashflows, dates)`
  - `rate`: The discount rate to apply to the cash flows.
  - `cashflows`: An array of cash flow amounts. These can be positive (inflows) and negative (outflows).
  - `dates`: An array of dates corresponding to the cash flows. The first date in the array is considered the start of
    the schedule.

- **Example Usage:**
  - `=XNPV(0.05, {-10000, 2750, 4250, 3250, 2750}, {DATE(2023, 1, 1), DATE(2023, 6, 1), DATE(2024, 1, 1), DATE(2024, 6, 1), DATE(2025, 1, 1)})`
  calculates the net present value of the cash flows given a 5% discount rate and their respective dates.
  - `=XNPV(A1, A2:A6, B2:B6)` computes the NPV using the discount rate in `A1`, cash flow data from `A2:A6`, and dates
    from `B2:B6`.

## Y

### [YIELD](./financial-functions/yield.md)
Calculates the annual yield of a security that pays periodic interest.

- **Purpose:** This function is used to compute the annualized yield of a security that pays interest periodically,
  based on
  the settlement date, maturity date, rate, price, redemption, frequency, and basis.

- **Formula:** `YIELD(settlement, maturity, rate, pr, redemption, frequency, [basis])`
  - `settlement`: The date when the security is purchased or settled. This is the **start date** of the investment.
  - `maturity`: The date when the security matures.
  - `rate`: The annual coupon rate of the security (as a decimal or percentage).
  - `pr`: The price of the security per $100 face value.
  - `redemption`: The redemption value per $100 face value.
  - `frequency`: The number of interest payments per year. Valid values are:
    - `1` for annual
    - `2` for semi-annual
    - `4` for quarterly
  - `basis` (optional): The day count basis to use. Defaults to `0`. Valid values are:
    - `0` for US (NASD) 30/360
    - `1` for actual/actual
    - `2` for actual/360
    - `3` for actual/365
    - `4` for European 30/360

- **Example Usage:**
  - `=YIELD(DATE(2023, 1, 15), DATE(2028, 1, 15), 0.05, 95.0, 100.0, 2)` calculates the annual yield of a security
    purchased
    on January 15, 2023, with a maturity date of January 15, 2028, a 5% annual coupon rate, a price
    of $95.00, a redemption
    value of $100.00, and semi-annual interest payments.
  - `=YIELD(A1, A2, A3, A4, A5, A6, A7)` computes the annual yield using settlement and maturity dates in `A1` and `A2`,
    the
    coupon rate in `A3`, the price in `A4`, the redemption value in `A5`, the frequency in `A6`, and the day count basis
    in `A7`.

### [YIELDDISC](./financial-functions/yield_disc.md)
Calculates the annual yield of a discounted security (a security that doesn't pay periodic interest but is issued at a
discount and matures at face value).

- **Purpose:** This function is used to compute the annualized yield of a discounted security based on its settlement
  date, maturity date, price, and redemption value.

- **Formula:** `YIELDDISC(settlement, maturity, pr, redemption, [basis])`
  - `settlement`: The date when the discounted security is purchased or settled. This is the **start date** of the
    investment.
  - `maturity`: The date when the discounted security matures.
  - `pr`: The price of the discounted security per $100 face value.
  - `redemption`: The redemption value per $100 face value (usually $100).
  - `basis` (optional): The day count basis to use. Defaults to `0`. Valid values are:
    - `0` for US (NASD) 30/360
    - `1` for actual/actual
    - `2` for actual/360
    - `3` for actual/365
    - `4` for European 30/360

- **Example Usage:**
  - `=YIELDDISC(DATE(2023, 1, 15), DATE(2023, 7, 15), 98.5, 100)` calculates the annual yield for a discounted security
    purchased on January 15, 2023, with a maturity date of July 15, 2023, a price of $98.50, and a redemption value of $
    100.
  - `=YIELDDISC(A1, A2, A3, A4, A5)` computes the yield using the settlement date in `A1`, the maturity date in `A2`,
    the price in `A3`, the redemption value in `A4`, and the basis in `A5`.

### [YIELDMAT](./financial-functions/yield_mat.md)
Calculates the annual yield of a security that pays interest at maturity.

- **Purpose:** This function is used to compute the annualized yield of a security that pays interest at maturity, based
  on its settlement date, maturity date, issue price, redemption value, and day count basis.

- **Formula:** `YIELDMAT(settlement, maturity, issue, rate, pr, [basis])`
  - `settlement`: The date when the security is purchased or settled. This is the **start date** of the investment.
  - `maturity`: The date when the security matures.
  - `issue`: The date when the security was originally issued.
  - `rate`: The annual coupon rate of the security (as a decimal or percentage).
  - `pr`: The price of the security per $100 face value.
  - `basis` (optional): The day count basis to use. Defaults to `0`. Valid values are:
    - `0` for US (NASD) 30/360
    - `1` for actual/actual
    - `2` for actual/360
    - `3` for actual/365
    - `4` for European 30/360

- **Example Usage:**
  - `=YIELDMAT(DATE(2023, 1, 15), DATE(2028, 1, 15), DATE(2020, 1, 15), 0.05, 95.0, 0)` calculates the annual yield of a
    security that was issued on January 15, 2020, purchased on January 15, 2023, with a maturity date of January 15,
    2028, a 5% annual coupon rate, a price of $95.00, and using the US (NASD) 30/360 day count basis.
  - `=YIELDMAT(A1, A2, A3, A4, A5, A6)` computes the annual yield using settlement and maturity dates in `A1` and `A2`,
    the issue date in `A3`, the coupon rate in `A4`, the price in `A5`, and the day count basis in `A6`.