<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DISC Function

The `DISC` function in Excel calculates the **discount rate** for a financial instrument, such as a Treasury bill or
bond, that is sold at a discount and does **not pay periodic interest**. This is often used for short-term securities
like T-bills where the return comes purely from the difference between the instrument's face value and its purchase
price.

## Key Features of DISC:

- Returns the annualized discount rate based on the settlement date, maturity date, price, and redemption value.
- Helps evaluate the profitability of short-term, non-interest-bearing securities.
- Uses actual or specified day count conventions for precise calculations.

## Syntax:

```plaintext
DISC(settlement, maturity, price, redemption, [basis])
```

### Arguments:

- **settlement**: The date when the security is purchased or settled. (Must be a valid date.)
- **maturity**: The date when the security matures or is redeemed. (Must be after the settlement date.)
- **price**: The price paid for the security (as a percentage of face value).
- **redemption**: The redemption value of the security (generally 100% of face value).
- **basis** (optional): The day count basis to use for the calculation:
    - `0`: US (NASD) 30/360 (default).
    - `1`: Actual/actual.
    - `2`: Actual/360.
    - `3`: Actual/365.
    - `4`: European 30/360.

## How It Works:

1. The function calculates the discount rate based on the following formula:

   $$ \text{Discount Rate} = \frac{\text{Redemption Value} - \text{Price}}{\text{Redemption Value}} \times \frac{\text{Actual Days in Year}}{\text{Days to Maturity}} $$

    - The formula annualizes the discount rate depending on the day count convention.

2. It ensures the correct relationship between the settlement and maturity dates, as well as calculations appropriate to
   the chosen basis.

## Examples:

### 1. Basic Discount Rate Calculation:

```excel
=DISC(DATE(2023,1,1), DATE(2023,6,30), 97, 100, 0)
```

**Result:** Calculates the discount rate for a security purchased on January 1, 2023, maturing on June 30, 2023, with a
price of 97 (97% of its face value) and a redemption value of 100 using the NASD 30/360 day count convention.

---

### 2. Using Actual/Actual Basis:

```excel
=DISC(DATE(2023,1,15), DATE(2023,7,15), 98, 100, 1)
```

**Result:** Returns the discount rate for a similar security using the actual/actual day count convention.

## Notes:

- The **settlement** and **maturity** dates must be valid Excel dates; otherwise, the function returns a `#VALUE!`
  error.
- If **price** or **redemption** is negative, or if **price** exceeds **redemption**, the function returns a `#NUM!`
  error.
- The **basis** argument allows flexibility for different financial practices globally.

## Applications:

- **Investment Analysis**: Commonly used by investors and analysts to evaluate short-term securities for their effective
  annual yield.
- **Treasury Bills**: Particularly useful for calculating the annual discount rate of T-bills or other similar financial
  instruments.
- **Fixed Income Securities**: Assists in assessing profitability for bonds or notes sold at a discount.

> **Tip:** Use `DISC` when you need to determine the discount rate of securities with no periodic interest payments. For
> bonds with regular interest, consider functions like `YIELD` or `PRICE`.