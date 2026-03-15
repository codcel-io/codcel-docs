<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## ISPMT Function

The `ISPMT` function in Excel calculates the **interest payment** for a given period of an investment or loan based on a
constant rate of interest and periodic payments. Unlike other financial functions such as `IPMT`, which includes
compound interest, `ISPMT` assumes a linear amortization of payments, where the interest is calculated linearly across
the periods.

This function is particularly useful when analyzing interest payments in scenarios involving straight-line depreciation
for financial instruments or loans.

### Key Features of ISPMT:

- Computes the interest payment for a specific period.
- Assumes the principal is linearly amortized (equally repaid) over the defined term.
- Useful for seeing how interest amounts decline over time.

### Syntax:

```plaintext
ISPMT(rate, per, nper, pv)
```

- **rate**: The interest rate for the investment or loan per period.
- **per**: The period for which you want to calculate the interest payment. Should be an integer between 1 and `nper`.
- **nper**: The total number of payment periods for the investment or loan.
- **pv**: The present value of the investment or the loan amount (principal).

### Examples:

1. `=ISPMT(5%/12, 1, 60, -10000)`  
   Calculates the interest payment for the 1st month of a 60-month loan with an annual interest rate of 5% and a loan
   amount of $10,000. Interest rate is divided by 12 to convert it to monthly periods.  
   **Result**: `-41.6667`

2. `=ISPMT(0.08, 10, 20, -5000)`  
   Computes the interest payment for the 10th period of a loan with 20 total periods, an annual interest rate of 8%, and
   a loan principal of $5,000.  
   **Result**: `-150`

3. `=ISPMT(3.5%/4, 4, 16, 20000)`  
   Calculates the interest payment for the 4th quarter of a 16-quarter investment with an annual interest rate of 3.5%
   and a principal of $20,000.  
   **Result**: `43.75`

### Notes:

- The `ISPMT` function only calculates **interest** and does not consider other components of a payment, such as
  principal.
- Values for **pv** (present value) should be expressed as negative for loans (cash outflows) and positive for
  investments (cash inflows).
- If **per** is less than 1 or greater than **nper**, the function returns an error (`#NUM!`).
- Ensure the **rate** matches the period. For example, if you're using monthly periods, divide the annual interest rate
  by 12.

> **Tip**: Use `ISPMT` to understand how the interest payment changes over time when the principal is paid off
> incrementally (non-compounding).