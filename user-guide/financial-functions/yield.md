<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## YIELD Function

The `YIELD` function in Excel calculates the **yield on a security** that pays periodic interest, such as a bond. It
takes into account factors like the bond's price, face value, coupon payment, settlement date, and maturity date to
provide the annualized yield (percentage return) for an investor.

### Key Features of YIELD:

- Computes the annual yield, which represents the return on investment for a bond or similar security.
- Based on periodic coupon payments and the difference between face value and purchased price.
- Handles bonds with both regular (e.g., semiannual interest) and irregular (first/last period) payment schedules.

### Syntax:

```plaintext
YIELD(settlement, maturity, rate, pr, redemption, frequency, [basis])
```

- **settlement**: The date the bond is purchased (settlement date).
    - Must be later than the issue date.
- **maturity**: The maturity date when the bond expires and the principal is repaid.
- **rate**: The annual coupon rate of the bond (e.g., `0.06` for 6%).
- **pr**: The price of the bond per $100 face value.
- **redemption**: The redemption value of the bond per $100 face value (often `100`).
- **frequency**: The number of coupon payments per year.
    - Use `1` for annual, `2` for semiannual, `4` for quarterly.
- **[basis]** *(optional)*: The day count basis for the calculation.
    - Defaults to `0` (US 30/360 system).
    - Other options: `1` (actual/actual), `2` (actual/360), `3` (actual/365), `4` (European 30/360).

### Examples:

1. **Basic Yield Calculation**:
   `=YIELD(DATE(2023,4,1), DATE(2033,4,1), 0.06, 95, 100, 2, 0)`  
   Calculates the yield of a bond purchased on April 1, 2023, maturing on April 1, 2033, with:
    - An annual coupon rate of 6%,
    - A purchase price of $95,
    - A redemption value of $100 per $100 face value, and
    - Semiannual payments.  
      **Result**: `0.0646` (approximately 6.46% annualized yield).

2. **Quarterly Payment Scenario**:
   `=YIELD(DATE(2023,6,1), DATE(2028,6,1), 0.05, 98.5, 100, 4, 1)`  
   Computes the annual yield for a 5-year bond with quarterly coupon payments, purchased for $98.50 with a 5% annual
   coupon rate.  
   **Result**: `0.0532` (approximately 5.32% annualized yield).

### Notes:

- **Interpretation**: The result represents the effective annual yield, factoring in the bond's purchase price, coupon
  rate, and payment frequency. A higher yield often implies higher returns but may also indicate higher risk.
- **Error values**:
    - `#NUM!`: Indicates invalid or unrealistic input values (e.g., settlement date after maturity date, negative
      price).
    - `#VALUE!`: Occurs if non-numeric data is input or invalid date entries are provided.
- **Usage Tips**:
    - Double-check bond prices and input dates to ensure accuracy.
    - Be cautious when using different day-count conventions (`basis`), as they may slightly impact the result.
    - The settlement and maturity dates must be entered using Excel's date format (e.g., `DATE(year, month, day)`).

### Formula Explanation:

The `YIELD` function computes the annual yield of a bond considering the pricing and interest payments. It uses an
iterative calculation to solve for the interest rate (`yield`) that equates the bond’s present value to its price:

```plaintext
Price = Σ [Coupon Payment / (1 + Yield/frequency)^(t * frequency)] + Redemption Value / (1 + Yield/frequency)^(n * frequency)
```

Where:

- `Coupon Payment`: Interest paid periodically (Face Value × Annual Coupon Rate ÷ Frequency).
- `t`: The payment number (e.g., 1st, 2nd, etc.).
- `n`: Total number of payments over the bond's life.

> **Comparison to RATE**:
> - Use `YIELD` to directly compute the return on bonds with periodic interest payments.
> - The `RATE` function is more generic and calculates the interest rate on loans or investments, given payment amounts
    and schedule details.