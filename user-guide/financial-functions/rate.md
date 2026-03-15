<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RATE Function

The `RATE` function in Excel calculates the **interest rate per period** required to pay off a loan or to reach a
specified future value of an investment, given constant payments and a consistent number of periods. This function is
useful for determining periodic loan or investment rates based on the financial conditions provided.

### Key Features of RATE:

- Determines the rate of return required for an investment or loan.
- Useful in loan repayment analysis or investment forecasting.
- Works with consistent periodic cash flows and a fixed repayment/investment schedule.

### Syntax:

```plaintext
RATE(nper, pmt, pv, [fv], [type], [guess])
```

- **nper**: The total number of payment periods for the loan or investment.
- **pmt**: The payment made per period. This value must generally include both principal and interest and is typically
  entered as a negative value (representing cash outflow).
- **pv**: The present value, or the principal amount of the loan or investment (positive for principal, negative for
  investment).
- **[fv]** *(optional)*: The future value, or the cash balance desired after the last payment. Defaults to `0` if
  omitted.
- **[type]** *(optional)*: Indicates when the payments are due:
    - `0` (default) for payments made at the **end** of the period.
    - `1` for payments made at the **beginning** of the period.
- **[guess]** *(optional)*: Your estimate of the interest rate. Defaults to `0.1` (10%) if omitted.

### Examples:

1. **Loan Interest Rate Calculation**:
   `=RATE(60, -377.42, 20000)`  
   Calculates the monthly interest rate for a loan of $20,000 (present value) with a monthly payment of $377.42 over 60
   months.
   **Result**: `0.004075` (or ~0.41% monthly interest rate).

2. **Investment Rate of Return**:
   `=RATE(10*4, -500, 0, 20000, 0)`  
   Determines the quarterly rate of return for an investment that pays $500 quarterly for 10 years, growing to $20,000
   after the period.
   **Result**: `0.0148` (or ~1.48% quarterly rate).

3. **Specified Payment Timing**:
   `=RATE(36, -200, 5000, 0, 1)`  
   Finds the monthly interest rate for a loan with $200 monthly payments for 3 years, with payments made at the *
   *beginning** of each period.
   **Result**: `0.0084` (or ~0.84% monthly interest rate).

### Notes:

- The **nper**, **pmt**, and **pv** should reflect consistent time units. For instance:
    - If payments are made monthly, **nper** should be in months.
    - If payments are annual, **nper** should be in years.
- The **guess** parameter can help the function converge to a correct result when interest rates are hard to estimate.
- If the RATE function returns `#NUM!`, it may indicate that:
    - No solutions fit the financial conditions provided.
    - You may need to adjust your **guess** to a closer estimate.
- Values:
    - **pmt** should typically be negative, representing payments made out of your account.
    - **pv** and **fv** can be positive (receiving money) or negative (paying money).

> **Tips**:
> - Use the **RATE** function to evaluate the cost of loans or the potential return of investments.
> - Combine with other Excel functions like `PMT`, `FV`, and `PV` for comprehensive financial analysis.
> - Double-check consistency in the units used for your input values (e.g., monthly/quarterly/annual time periods).