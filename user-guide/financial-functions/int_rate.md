<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# INTRATE Function

The `INTRATE` function in Excel calculates the **interest rate** for a fully invested security given the security's
purchase price, redemption value, and the duration of the investment (based on the number of days between settlement and
maturity dates). It is particularly useful when determining the rate of return on investments like treasury bills or
zero-coupon bonds.

## Key Features of INTRATE:

- Computes the annualized interest rate for a security based on its purchase price and redemption value.
- Suitable for calculating interest rates when the full principal is invested upfront.
- Adjusts for the length of the investment in days, making it flexible for short-term securities.

## Syntax:

```plaintext
INTRATE(settlement, maturity, investment, redemption, [basis])
```

### Arguments:

1. **settlement**: The date on which the security is purchased (settlement date). This is provided as a valid date in
   Excel.
2. **maturity**: The date when the security matures (maturity date).
3. **investment**: The initial amount (or purchase price) of the security.
4. **redemption**: The amount received upon maturity (or the redemption value of the security).
5. **basis** *(optional)*: The day count basis used for the calculation. Default is `0`. The basis options are as
   follows:
    - `0` or omitted: Actual/360
    - `1`: Actual/Actual
    - `2`: Actual/360
    - `3`: Actual/365
    - `4`: European 30/360

### How It Works:

1. The formula calculates the interest rate using the following equation:

   ```plaintext
   Interest Rate = (Redemption - Purchase Price) / (Purchase Price * (DSM / B))
   ```

   Where:
    - **Redemption**: The redemption value of the security.
    - **Purchase Price**: The initial investment.
    - **DSM**: The duration in days between `settlement` and `maturity`.
    - **B**: The year basis (e.g., 360 or 365 days, depending on the provided `basis` argument).

## Examples:

### 1. Calculate the Interest Rate for a Treasury Bill:

```excel
=INTRATE(DATE(2023, 1, 1), DATE(2023, 12, 31), 5000, 5200)
```

**Result:** `0.08` or `8%`

This calculates the annualized interest rate for a security purchased on January 1, 2023, with a maturity date of
December 31, 2023, an initial investment of $5,000, and a redemption value of $5,200. The default Actual/360 day count
is used.

---

### 2. Use a Different Basis (Actual/Actual):

```excel
=INTRATE(DATE(2023, 1, 1), DATE(2023, 7, 1), 1000, 1020, 1)
```

**Result:** `0.0399` or `3.99%`

This calculates the annualized interest rate for an investment of $1,000 that matures at $1,020 after 6 months (183
days), using the Actual/Actual day count basis.

---

### 3. Include Non-Annual Basis (European 30/360):

```excel
=INTRATE(DATE(2023, 1, 15), DATE(2023, 4, 15), 2000, 2100, 4)
```

**Result:** `0.20` or `20%`

This computes the interest rate for a three-month security purchased for $2,000, maturing at $2,100, using the European
30/360 basis.

---

### Notes:

- Dates provided for **settlement** and **maturity** must be valid Excel date formats. Use `DATE(year, month, day)` or
  cell references containing correct dates.
- Ensure the **investment** and **redemption** values are accurate and reflect the security terms.
- **Basis** determines the length of a year (360 days, 365 days, etc.) and influences the calculation accuracy based on
  conventions of financial instruments.

---

## Applications:

- **Treasury and Government Bonds**: Determine short-term or long-term interest rates on treasury securities.
- **Zero-Coupon Bonds**: Calculate rates for bonds with no periodic interest payments.
- **Money Market Instruments**: Useful for estimating rates for deposits, CDs, or other financial instruments.
- **Investment Analysis**: Compare the annualized return rates of various securities with differing maturities and
  initial investments.

> **Tip:** Always ensure the **basis** aligns with the conventions of your financial instrument to ensure accuracy.