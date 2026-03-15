<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ODDFPRICE Function

The `ODDFPRICE` function in Excel calculates the price per $100 face value of a security that has an **odd (irregular)
first period**. This is commonly used when dealing with bonds or securities where the first interest payment period is
not of standard length.

This function is particularly useful in financial analysis for accurately pricing bonds or securities with irregular
first periods, which may occur when issuing a bond in the middle of a standard coupon period.

---

### Key Features of ODDFPRICE:

- Determines the price of a security with a non-standard, shorter, or longer first coupon period.
- Accounts for factors such as settlement date, maturity, yield, coupon rate, and day count basis.
- Helps in valuing securities consistently across irregular periods.

---

### Syntax:

```plaintext
ODDFPRICE(settlement, maturity, issue, first_coupon, rate, yld, redemption, frequency, [basis])
```

#### Arguments:

1. **settlement**: The settlement date of the security (the date the buyer acquires the security).
    - Must be a valid date in Excel.
    - The settlement date must be earlier than the maturity date.

2. **maturity**: The maturity date of the security (the date the principal will be repaid).
    - Must also be a valid date in Excel.

3. **issue**: The date the security was originally issued.
    - Represents when the security starts accruing interest.

4. **first_coupon**: The date of the first coupon payment after the issuance.
    - Reflects the irregularity in the first period.

5. **rate**: The annual coupon rate of the security.
    - Provided as a percentage (e.g., 5% = 0.05).

6. **yld**: The annual yield of the security.
    - Expressed as a percentage (e.g., 6% = 0.06).

7. **redemption**: The redemption value per $100 face value of the security (usually $100).

8. **frequency**: The number of coupon payments per year.
    - Acceptable values:
        - `1`: Annual
        - `2`: Semi-Annual
        - `4`: Quarterly

9. **[basis]** *(optional)*: The day-count convention to use.
    - Possible values:
        - `0` or omitted: US (NASD) 30/360
        - `1`: Actual/Actual
        - `2`: Actual/360
        - `3`: Actual/365
        - `4`: European 30/360

---

### Examples:

1. **Semi-Annual Bond with Odd First Period**
   ```excel
   =ODDFPRICE(DATE(2023,10,1), DATE(2030,10,1), DATE(2023,1,1), DATE(2023,4,1), 0.05, 0.06, 100, 2, 0)
   ```  
   Calculates the price of a bond where:
    - Issue date: `1-Jan-2023`
    - First coupon: `1-Apr-2023`
    - Maturity: `1-Oct-2030`
    - Coupon rate: `5%`
    - Yield: `6%`
    - Redemption: `$100`
    - Payments are semi-annual (`2`)  
      **Result**: `$96.54` *(example value).*

2. **Quarterly Bond Example**
   ```excel
   =ODDFPRICE(DATE(2023,9,15), DATE(2027,9,15), DATE(2023,1,1), DATE(2023,4,1), 0.04, 0.045, 100, 4, 1)
   ```  
   Computes the price for a bond where interest is paid quarterly (`4`) with an irregular first period.

---

### Notes:

- **Settlement and maturity dates**:
    - Ensure that they are valid and entered using Excel's `DATE` function or as serial numbers.
    - Settlement must be earlier than maturity; otherwise, `#NUM!` is returned.

- **Irregular periods**:
    - An irregular first coupon period typically results when the time to the first payment is shorter or longer than
      standard coupon intervals. Use this function to model these irregularities accurately.

### Common Errors:

1. **`#NUM!`**: Occurs when:
    - The `settlement` date is not earlier than the `maturity` date.
    - Invalid or conflicting parameters (e.g., frequency not `1`, `2`, or `4`).

2. **`#VALUE!`**: Occurs if the dates are invalid or not recognized by Excel.

> **Tip**: Use `ODDFPRICE` together with other pricing functions like `ODDLLPRICE` (for odd last periods) to handle
> bonds with irregular coupon dates effectively.
---