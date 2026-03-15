<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DURATION Function

The `DURATION` function in Excel calculates the **Macauley duration** of a security with periodic interest payments.
This measure expresses the weighted average time until a security's cash flows are paid, helping assess interest rate
sensitivity.

## Key Features of DURATION:

- Computes the Macauley duration for securities with a consistent interest payment schedule.
- Useful for analyzing the price volatility of bonds relative to changes in interest rates.
- Requires detailed input on settlement, maturity, coupon rate, yield, frequency, and basis.

## Syntax:

```plaintext
DURATION(settlement, maturity, coupon, yield, frequency, [basis])
```

### Arguments:

- **settlement**: The date when the security is purchased or settled. Entered as a date in Excel.
- **maturity**: The date when the security expires. Must also be a valid date.
- **coupon**: The annual coupon interest rate of the security (as a percentage). For example, 5% is entered as `0.05`.
- **yield**: The annual yield of the security (as a percentage). For example, 6% is entered as `0.06`.
- **frequency**: The number of coupon payments per year:
    - `1`: Annual payments.
    - `2`: Semi-annual payments.
    - `4`: Quarterly payments.
- **basis** *(optional)*: The day-count basis for the calculation. The options are:
    - `0` or omitted: US (NASD) 30/360.
    - `1`: Actual/actual.
    - `2`: Actual/360.
    - `3`: Actual/365.
    - `4`: European 30/360.

## How It Works:

1. The function determines the present value of the bond's cash flows and computes the holding period's weighted average
   for cash flows.
2. Macauley duration reflects the sensitivity of the bond’s price to interest rate changes.

## Examples:

### 1. Calculate Semi-Annual Macauley Duration:

```excel
=DURATION(DATE(2023,1,1), DATE(2033,1,1), 0.05, 0.06, 2, 0)
```

**Result:** `7.62`

This computes the Macauley duration of a bond with:

- Issue date: January 1, 2023.
- Maturity date: January 1, 2033.
- Annual coupon rate: 5%.
- Yield: 6%.
- Frequency of payments: Semi-annual.
- Basis: US 30/360.

---

### 2. Calculate Annual Duration with Actual/Actual Basis:

```excel
=DURATION(DATE(2024,5,15), DATE(2044,5,15), 0.04, 0.03, 1, 1)
```

**Result:** `13.45`

This computes the Macauley duration of a bond with annual payments, actual/actual basis, and a 4% coupon rate.

---

### Notes:

- If **settlement** is after **maturity**, the function returns a `#NUM!` error.
- Incorrect or invalid dates result in a `#VALUE!` error.
- Ensure the **frequency** and **basis** accurately correspond to the security's terms to avoid miscalculations.

## Applications:

- **Interest Rate Risk Measurement**: The lower the Macauley duration, the less sensitive a bond is to interest rate
  changes.
- **Bond Portfolio Management**: Helps evaluate portfolio duration to match or hedge interest rate movements.
- **Asset-Liability Matching**: Used to align the duration of assets and liabilities in financial institutions.

> **Tip:** Use the `YIELD` function in Excel to calculate the annual yield of a bond, which can then be used as input to
> the `DURATION` function for precision calculations.