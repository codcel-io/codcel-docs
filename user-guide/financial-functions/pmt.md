<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PMT Function

The `PMT` function in Excel calculates the **payment amount** for a loan or an investment based on constant payments and
a constant interest rate. This function is commonly used for financial planning, such as determining loan payments or
savings contributions.

### Key Features of PMT:

- Computes the periodic payment required to achieve a financial target or pay off a loan.
- Useful for loan repayment calculations, mortgage planning, or investment scenarios.
- Assumes regular, fixed payments and a constant interest rate over the term of the loan or investment.

### Syntax:

```plaintext
PMT(rate, nper, pv, [fv], [type])
```

- **rate**: The interest rate per period (expressed as a decimal). For example, a 5% annual interest rate would be
  `0.05`.
- **nper**: The total number of payment periods (e.g., 12 months for a 1-year loan with monthly payments).
- **pv**: The present value (e.g., initial loan amount or investment value).
- **[fv]** *(optional)*: The future value. Defaults to `0` if omitted, often used for loans.
- **[type]** *(optional)*: The timing of the payment:
    - `0` (default) for payments made at the end of each period.
    - `1` for payments made at the beginning of each period.

### Examples:

1. **Loan Payment**:
   `=PMT(0.05/12, 60, -20000)`  
   Calculates the monthly payment for a $20,000 loan at 5% annual interest, paid over 5 years.  
   **Result**: `-$377.42` (negative value indicates outgoing payment).

2. **Savings Contribution**:
   `=PMT(0.03/4, 10*4, 0, 50000)`  
   Determines the quarterly contribution needed to save $50,000 over 10 years, with a quarterly interest rate of 3%.  
   **Result**: `-$1,078.02`.

3. **Future Value with Regular Payments**:
   `=PMT(0.06/12, 24, 0, 10000, 1)`  
   Determines the monthly payment required to accumulate $10,000 within 2 years, assuming a 6% annual interest rate and
   payments made at the start of each month.  
   **Result**: `-$405.45`.

### Notes:

- The **rate** must align with the period frequency. For example:
    - Use the monthly interest rate for monthly payments.
    - Divide the annual rate by `12` for monthly calculations.
- The **pv** (present value) is typically entered as a negative value for loans (cash outflow), but savings or
  investments use a positive value.
- The result is returned as a negative value to indicate an outgoing payment. You can use `ABS()` to display it as a
  positive number if needed.

> **Tips**:
> - Use the `PMT` function along with `IPMT` (Interest Payment) and `PPMT` (Principal Payment) to analyze the breakdown
    of payments in each period.
> - Double-check that the **rate** and **nper** correspond to the same time units (e.g., match monthly interest rates
    with the number of months for payment).