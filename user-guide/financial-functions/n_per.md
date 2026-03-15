<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NPER Function

The `NPER` function in Excel calculates the **number of periods** required to pay off a loan or reach a financial goal,
based on constant payments and a fixed interest rate. This function is commonly used in financial planning to determine
how long it will take to repay a loan or achieve a target investment value.

This function is particularly useful when assessing loan durations or planning savings/investment strategies.

---

### Key Features of NPER:

- Calculates the total number of payment periods for a loan or investment.
- Works with fixed interest rates and regular payment amounts.
- Useful for financial planning, such as determining time needed to repay loans or achieve savings goals.

---

### Syntax:

```plaintext
NPER(rate, pmt, pv, [fv], [type])
```

- **rate**: The interest rate per period.
    - Must be provided as a decimal (e.g., 5% = 0.05).
    - If annual interest is given, divide it by the number of periods per year (e.g., for monthly, divide by 12).
- **pmt**: The payment made each period.
    - Should be a fixed number and include principal and interest.
    - Enter as a negative value for outgoing payments.
- **pv**: The present value, or the loan amount/investment's current value.
    - For loans, this is typically the initial amount borrowed.
- **[fv]** *(optional)*: The future value you want to achieve after the last payment.
    - Default is `0` (e.g., for a fully paid-off loan).
    - Non-zero values are used for investments or goals.
- **[type]** *(optional)*: Indicates when payments are made.
    - `0` (default): End of period.
    - `1`: Beginning of period.

---

### Examples:

1. `=NPER(5%/12, -200, 5000)`  
   Calculates the number of months needed to repay a loan of `$5,000` with fixed monthly payments of `$200` and an
   annual interest rate of `5%`.  
   **Result**: `26.15` months *(example value).*

2. `=NPER(0.04, -100, -500, 1000)`  
   Determines how many periods are required to grow an investment from `-$500` to `$1,000` with an annual return rate of
   `4%` and `-$100` outgoing payments.  
   **Result**: `8.99` periods *(example value).*

3. `=NPER(6%/12, -300, 10000, 0, 1)`  
   Finds the number of periods required to repay a loan of `$10,000` with monthly payments of `$300`, a `6%` annual
   interest rate, starting payments at the beginning of the period.  
   **Result**: `36.74` months *(example value).*

---

### Notes:

- The **rate**, **pmt**, and **pv** arguments must be consistent in terms of the period. For example, if payments are
  monthly, the interest rate should be the monthly rate (annual rate divided by 12).
- If the **pmt** value is zero, the function will return a `#NUM!` error because regular payments are required to
  calculate the number of periods.
- For loan calculations, the **pmt** should generally be negative to represent outgoing payments.
- The function assumes that payments are fixed and occur at regular intervals.

> **Tip**: Use the `NPER` function when you need to plan the duration of loans or savings over time. It is especially
> helpful in comparing payment schedules for different financial products.

---