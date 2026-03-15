<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## YIELDDISC Function

The `YIELDDISC` function in Excel calculates the **annual yield of a discounted (non-interest bearing) security**. This
type of security is sold at a price below its face value, and the yield is derived based on the purchase price, face
value, settlement date, and maturity date.

### Key Features of YIELDDISC:

- Computes the yield for securities purchased at a discount without periodic interest payments.
- Suitable for instruments such as Treasury Bills or zero-coupon bonds.
- Uses the straight-line method to calculate the annualized yield.

### Syntax:

```plaintext
YIELDDISC(settlement, maturity, pr, redemption, [basis])
```

- **settlement**: The date the security is bought (settlement date).
    - Must be entered as a valid date and occur before the maturity date.
- **maturity**: The date the security matures (maturity date).
    - This is when the face value (redemption value) is paid back.
- **pr**: The price of the security per $100 face value.
    - Typically below 100 since the security is sold at a discount.
- **redemption**: The redemption value of the security per $100 face value.
    - Often `100`.
- **[basis]** *(optional)*: The day count basis used for the calculation.
    - Defaults to `0` (US 30/360 standard).
    - Other options:
        - `1`: Actual/actual
        - `2`: Actual/360
        - `3`: Actual/365
        - `4`: European 30/360

### Examples:

1. **Annual Yield for a Discount Security**:
   `=YIELDDISC(DATE(2023,1,1), DATE(2023,12,31), 95, 100, 0)`  
   Calculates the yield for a security purchased on January 1, 2023, at $95, with a redemption value of $100 on December
   31, 2023.  
   **Result**: `0.0526` (approximately 5.26% annualized yield).

2. **Custom Day-Count Basis**:
   `=YIELDDISC(DATE(2023,3,15), DATE(2024,3,14), 98, 100, 1)`  
   Computes the yield of a security purchased for $98 with a redemption value of $100, using an actual/actual day-count
   basis.  
   **Result**: `0.0204` (approximately 2.04% annualized yield).

### Notes:

- **Error values**:
    - `#NUM!`: Happens when:
        - The settlement date is after the maturity date.
        - Invalid or unrealistic financial values are input (e.g., negative price or redemption).
    - `#VALUE!`: Occurs if non-numeric or incorrect date inputs are provided.
- **Day-Count Basis Impact**:
    - The selected `basis` affects the yield calculation by determining how days between settlement and maturity are
      counted.
    - For example:
        - Actual/actual (`1`) includes exact calendar days.
        - 30/360 (`0`) assumes standardized 30-day months and 360-day years.

### Formula Explanation:

The `YIELDDISC` function calculates the annualized yield using the formula:

```plaintext
Yield = ((Redemption - Price) / Price) * (Basis Days / Actual Days)
```

Where:

- **Redemption**: Face value of the security.
- **Price**: Purchase price of the security.
- **Basis Days**: Assumed days in a year based on the selected day-count basis.
- **Actual Days**: Number of days from settlement to maturity.

### Applications:

- **Use Case**: The `YIELDDISC` function is particularly useful for investors analyzing short-term treasury bills or
  zero-coupon bonds, where returns are derived solely from the discount between the purchase price and the face value.