<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## YIELDMAT Function

The `YIELDMAT` function in Excel calculates the **annual yield of a security that pays interest at maturity**. This is
commonly used for securities such as bonds that pay accrued interest and principal repayment on their maturity date.

### Key Features of YIELDMAT:

- Computes the yield for securities that combine principal repayment and accumulated interest at maturity.
- Applicable to bonds that do not make periodic interest payments but pay interest along with the principal at the end
  of their life.
- Uses the **actual number of days between dates** for the calculation of the yield.

### Syntax:

```plaintext
YIELDMAT(settlement, maturity, issue, rate, pr, [basis])
```

- **settlement**: The date on which the security is purchased (settlement date).
    - Must be a valid date and fall **after the issue date** but **before the maturity date**.
- **maturity**: The date on which the security matures (maturity date).
    - This is when the principal and interest are repaid.
- **issue**: The date when the security was originally issued (issue date).
    - Used alongside `settlement` and `maturity` to determine the yield.
- **rate**: The annual coupon rate of the security, expressed as a decimal.
    - For example, 6% annual rate is input as `0.06`.
- **pr**: The price of the security per $100 face value.
    - This is the purchase price of the security.
- **[basis]** *(optional)*: The day count basis used for the calculation.
    - Defaults to `0` (US 30/360 standard).
    - Other options:
        - `1`: Actual/actual
        - `2`: Actual/360
        - `3`: Actual/365
        - `4`: European 30/360

### Examples:

1. **Calculating Yield of a Security**:
   `=YIELDMAT(DATE(2023,1,1), DATE(2025,1,1), DATE(2020,1,1), 0.05, 98, 0)`  
   Calculates the yield for a security with an issue date of January 1, 2020, a settlement date of January 1, 2023, a
   maturity date of January 1, 2025, a 5% annual rate, purchased at $98, using a 30/360 day count basis.  
   **Result**: `0.0538` (approximately 5.38% annualized yield).

2. **Custom Day-Count Basis Example**:
   `=YIELDMAT(DATE(2023,5,15), DATE(2026,5,15), DATE(2020,5,15), 0.04, 96, 2)`  
   Computes the annual yield of a security with a 4% rate, a price of $96, issued on May 15, 2020, purchased on May 15,
   2023, and maturing on May 15, 2026, using an Actual/360 day count basis.  
   **Result**: `0.05306` (approximately 5.31% annualized yield).

### Notes:

- **Error values**:
    - `#NUM!`: Happens when:
        - Settlement date is earlier than or the same as the issue date.
        - Maturity date occurs before the settlement date.
        - Invalid or unrealistic financial values (e.g., negative price or rates).
    - `#VALUE!`: Occurs if non-numeric or incorrect date inputs are used.
- **Day-Count Basis Impact**:
    - Changing the `basis` parameter affects how days between the relevant dates are counted.
    - For example:
        - `Actual/actual` (`1`) uses exact calendar days.
        - `30/360` (`0`) assumes standardized months and years.

### Formula Explanation:

The `YIELDMAT` function calculates the yield using the formula:

```plaintext
Yield = ((Redemption + Accrued Interest - Price) / Price) * (Basis Days / Actual Days)
```

Where:

- **Redemption** refers to the face value of the security.
- **Accrued Interest** is the interest earned from the issue date to the maturity date based on the annual rate.
- **Price** is the purchase price of the security.
- **Basis Days** represents the assumed number of days in a year (e.g., 360 or 365).
- **Actual Days** is the actual number of days between the settlement and maturity.

### Applications:

- **Use Case**: The `YIELDMAT` function is suited for analyzing investments in bonds or securities where both the
  interest and principal are paid at maturity, rather than periodic interest being provided.