<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ODDFYIELD Function

The `ODDFYIELD` function in Excel calculates the **yield** of a security with an **odd (irregular) first period**. This
is particularly useful when analyzing bonds or other securities where the initial coupon payment period is not of
standard length, resulting in irregular first cash flows.

This function assists in financial analysis by determining the effective annual return (yield) for securities with
irregular first coupon periods, enabling precise evaluation of returns.

---

### Key Features of ODDFYIELD:

- Determines the yield of a security with a shorter or longer first coupon period than usual.
- Considers important parameters such as settlement date, maturity date, issue date, first coupon payment, rate, price,
  redemption value, and day-count basis.
- Valuable for analyzing the return of bonds or securities with irregular periods.

---

### Syntax:

```plaintext
ODDFYIELD(settlement, maturity, issue, first_coupon, rate, pr, redemption, frequency, [basis])
```

#### Arguments:

1. **settlement**: The settlement date of the security (the date the buyer acquires it).
    - Must be a valid Excel date.
    - The settlement date must occur before the maturity date.

2. **maturity**: The maturity date of the security (the date the principal is repaid).
    - Must also be a valid Excel date.

3. **issue**: The original issue date of the security.
    - The date when interest starts accruing for the bond.

4. **first_coupon**: The date of the first coupon payment after issuance.
    - Specifies the irregularity of the first period.

5. **rate**: The annual coupon rate of the security.
    - Enter as a decimal (e.g., 5% is entered as `0.05`).

6. **pr**: The price of the security per $100 face value.
    - For example, if the bond costs $97.50, this value would be `97.50`.

7. **redemption**: The redemption (or face) value per $100 of the security (usually `100`).

8. **frequency**: Number of coupon payments per year.
    - Allowed values are:
        - `1`: Annual
        - `2`: Semi-Annual
        - `4`: Quarterly

9. **[basis]** *(optional)*: The day-count basis for calculating interest (default is `0` for US (NASD) 30/360).
    - Possible values:
        - `0`: US (NASD) 30/360 (default)
        - `1`: Actual/Actual
        - `2`: Actual/360
        - `3`: Actual/365
        - `4`: European 30/360

---

### Examples:

1. **Semi-Annual Bond with Odd First Period**
   ```excel
   =ODDFYIELD(DATE(2023,10,1), DATE(2030,10,1), DATE(2023,1,1), DATE(2023,4,1), 0.05, 96.50, 100, 2, 0)
   ```  
    - **Bond Details**:
        - Issue date: `1-Jan-2023`
        - First coupon: `1-Apr-2023`
        - Maturity date: `1-Oct-2030`
        - Coupon rate: `5%`
        - Purchase price: `$96.50`
        - Redemption value: `$100`
        - Payment frequency: Semi-Annual (`2`)
        - Day count basis: US (NASD) 30/360 (`0`)
    - **Result**: `5.62%` (example value).

2. **Quarterly Bond Yield with Irregular First Payment**
   ```excel
   =ODDFYIELD(DATE(2023,9,15), DATE(2027,9,15), DATE(2023,1,1), DATE(2023,4,10), 0.04, 97.00, 100, 4, 1)
   ```  
    - **Bond Details**:
        - Settlement date: `15-Sep-2023`
        - Maturity date: `15-Sep-2027`
        - Issue date: `1-Jan-2023`
        - First coupon: `10-Apr-2023`
        - Coupon rate: `4%`
        - Purchase price: `$97`
        - Redemption value: `$100`
        - Payment frequency: Quarterly (`4`)
        - Day count basis: Actual/Actual (`1`)
    - **Result**: `4.21%` (example value).

---

### Notes:

- **Settlement, maturity, and issue dates must be valid Excel dates**:
    - Use Excel's `DATE` function to ensure proper date formatting.
    - The settlement date must be before the maturity date, or Excel will return `#NUM!`.

- **Irregular first periods**:
    - The `ODDFYIELD` function is specifically tailored to calculate yields for bonds with irregular periods between the
      issue date and first coupon payment.

- **Use with Related Functions**:
    - Combine with `ODDFPRICE` for pricing bonds with irregular periods, ensuring accurate financial analysis.

---

### Common Errors:

1. **`#NUM!`**:
    - Occurs when:
        - The settlement date is not earlier than the maturity date.
        - Invalid parameters, such as an unsupported `frequency`.

2. **`#VALUE!`**:
    - Occurs if one or more dates or other arguments are invalid or unrecognized.

> **Tip**: Use `ODDFYIELD` to complement other bond analysis tools in financial modeling and to account for irregular
> payment schedules effectively.
---