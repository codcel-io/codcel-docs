<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ACCRINT Function

The `ACCRINT` function in Excel is used to calculate the **accrued interest** for a security that pays periodic interest. This function is useful for determining the amount of interest that has accumulated between the issue and settlement date based on the security's coupon payment schedule.

## Key Features of ACCRINT:

- Computes interest accrued up to a certain settlement date for a security that pays periodic interest.
- Useful for financial professionals dealing with fixed-income securities or bond valuations.
- Supports various day count conventions (e.g., Actual/360, Actual/365, etc.).
- Includes a `calc_method` parameter that determines whether to include the full first period or calculate it proportionally.

## Syntax:

```plaintext
ACCRINT(issue, first_interest, settlement, rate, par, frequency, [basis], [calc_method])
```

- **issue**: The date the security was issued.
- **first_interest**: The date of the first interest payment for the security.
- **settlement**: The date the security is purchased or settled by the buyer.
- **rate**: The annual coupon rate of the security.
- **par**: The par value (face value) of the security. Defaults to `1000` if omitted.
- **frequency**: The number of coupon payments per year:
    - `1` = Annual payments.
    - `2` = Semi-annual payments.
    - `4` = Quarterly payments.
- **[basis]**: (Optional) The day count basis to use. Defaults to `0`. The options are:
    - `0` = US (NASD) 30/360 (default).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.
- **[calc_method]**: (Optional) A logical value (TRUE or FALSE) that determines whether to include the full first period:
    - `TRUE` (or omitted) = Accrues interest from the issue date, even if it's before the first interest payment.
    - `FALSE` = Accrues interest only from the first interest payment date.

## How It Works:

The `ACCRINT` function computes the interest accrued using the formula based on the day count convention and number of coupon payments, as per the financial terms of the bond.

1. It calculates the interest for the time period between `issue` and `settlement` dates.
2. The function accounts for the interest period and divides the annual interest by the frequency of payments.
3. The `basis` parameter determines how days are counted in the year.
4. The `calc_method` parameter determines whether the first interest period is included fully or calculated proportionally.

## Examples:

### 1. Accrued Interest for Semi-annual Payments:

```excel
=ACCRINT(DATE(2023,1,1), DATE(2023,7,1), DATE(2023,4,1), 0.06, 1000, 2, 0)
```

**Result:** `15.00`.

### 2. Accrued Interest for Quarterly Payments:

```excel
=ACCRINT(DATE(2023,1,1), DATE(2023,4,1), DATE(2023,2,15), 0.08, 500, 4, 1)
```

**Result:** `5.11`.

### 3. Accrued Interest using Actual/360 Basis:

```excel
=ACCRINT(DATE(2022,1,1), DATE(2023,1,1), DATE(2022,12,1), 0.05, 100, 1, 2)
```

**Result:** `4.86`.

### 4. Accrued Interest with `calc_method = FALSE` (Proportional First Period):

```excel
=ACCRINT(DATE(2023,1,1), DATE(2023,7,1), DATE(2023,4,1), 0.06, 1000, 2, 0, FALSE)
```

**Result:** `15.00`.

## Notes:

- If the `issue`, `first_interest`, or `settlement` dates are not valid dates or if `settlement` occurs before `issue`, Excel returns a `#VALUE!` or `#NUM!` error.
- The **frequency** must be `1`, `2`, or `4`. Any other value will also result in an error.
- The **basis** parameter determines how the number of days in a year is calculated, impacting the accrued interest.
- The **calc_method** parameter affects whether interest is accrued for the entire first period (`TRUE`) or proportionally (`FALSE`).

## Applications:

- **Bond Valuation**: Quickly determine how much interest is owed between coupon payments for fixed-income security.
- **Financial Analysis**: Used in portfolio management and trading of interest-bearing securities.
- **Investment Accounting**: Helps calculate interest income for tax and audit purposes.

> **Tip:** When using the `ACCRINT` function, ensure all date inputs are valid Excel date values (e.g., `DATE(year, month, day)`), as invalid dates will prevent the function from working correctly.