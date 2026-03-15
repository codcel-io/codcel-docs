<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PPMT Function

The `PPMT` function in Excel calculates the **principal portion** of a payment for a given period in an amortized loan
or investment. This helps determine how much of a payment goes towards reducing the principal balance, as opposed to the
interest.

### Key Features of PPMT:

- Breaks down a payment into its **principal** component for a specific period.
- Useful for analyzing loan payments, tracking progress in repayment schedules, and understanding amortization
  structures.
- Works in conjunction with the `IPMT` (Interest Payment) function to fully analyze loan payment details.

### Syntax:

```plaintext
PPMT(rate, per, nper, pv, [fv], [type])
```

- **rate**: The interest rate per period (expressed as a decimal). For example, a 5% annual interest rate would be
  `0.05`.
- **per**: The specific payment period to calculate the principal portion for (must be between `1` and `nper`).
- **nper**: The total number of payment periods (e.g., 12 months for a 1-year loan with monthly payments).
- **pv**: The present value (e.g., current loan amount or investment value).
- **[fv]** *(optional)*: The future value. Defaults to `0` if omitted, commonly used for loans.
- **[type]** *(optional)*: The timing of the payment:
    - `0` (default) for payments made at the end of each period.
    - `1` for payments made at the beginning of each period.

### Examples:

1. **Principal Portion of a Loan Payment**:
   `=PPMT(0.05/12, 1, 60, -20000)`  
   Calculates the principal portion of the first monthly payment for a $20,000 loan with a 5% annual interest rate, to
   be paid over 5 years.  
   **Result**: `-$252.59` (negative value indicates outgoing payment).

2. **Tracking Loan Progress**:
   `=PPMT(0.05/12, 12, 60, -20000)`  
   Determines the amount of the 12th monthly payment that goes towards the principal for the same loan as above.  
   **Result**: `-$309.97`.

3. **Investment with Future Value**:
   `=PPMT(0.06/4, 8, 20, 0, 50000, 1)`  
   Calculates the principal portion of the 8th quarterly payment in an investment trying to accumulate $50,000 over 5
   years (20 quarters), with a 6% annual interest rate, and payments made at the start of the quarter.  
   **Result**: `-$2,201.12`.

### Notes:

- The **rate** and **nper** must align in terms of the time periods (e.g., use monthly interest rates with the number of
  months for payments).
- The **per** argument indicates the payment period you want to calculate the principal for. It must be an integer
  between `1` and `nper`.
- **pv** (present value) is typically entered as a negative value for loans (cash outflow), resulting in a negative
  output for outgoing payments.

> **Tips**:
> - Use the `PPMT` function alongside `IPMT` to understand how each payment is split between principal and interest.
> - Combine `PPMT` with `PMT` to create a full amortization schedule that outlines the reduction of principal and
    interest over the payment term.
> - Like `PMT`, the result of `PPMT` is negative to reflect an outgoing payment. You can wrap it with `ABS()` to display
    a positive value if desired.