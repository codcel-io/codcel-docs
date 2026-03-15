<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# IPMT Function

The `IPMT` function in Excel is used to calculate the **interest portion of a payment** for a given period of a loan or
an investment with constant periodic payments and a constant interest rate. This is particularly useful in financial
modeling and loan amortization schedules.

## Key Features of IPMT:

- Calculates the interest part of a payment for a specific period during the term of a loan or investment.
- Assists in separating loan repayments into **interest** and **principal** components.
- Useful for tracking loan payments, mortgage schedules, or investment analysis.

## Syntax:

```plaintext
IPMT(rate, per, nper, pv, [fv], [type])
```

- **rate**: The interest rate per period.
- **per**: The specific period for which you want to calculate the interest. Must be between `1` and `nper`.
- **nper**: The total number of payment periods in the loan or investment.
- **pv**: The present value (or principal) of the loan or investment.
- **[fv]** (Optional): The future value or cash balance desired after completing the last payment. Defaults to `0`.
- **[type]** (Optional): Indicates when payments are due:
    - `0` = End of the period (default).
    - `1` = Beginning of the period.

## How It Works:

1. Calculates the interest portion of a payment based on your input parameters.
2. The total payment combines **interest** (calculated by `IPMT`) and **principal** (the remainder of the payment).
3. It assumes consistent periodic payments throughout the term.

## Examples:

### 1. Monthly Loan Payment (End of Period):

```excel
=IPMT(5%/12, 1, 60, 30000)
```

**Result:** Returns the interest portion of the first payment for a loan of $30,000, with a 5% annual interest rate (
divided by 12 for monthly periods), over 60 months.

### 2. Quarterly Loan Payment with Future Value and Beginning Period Payments:

```excel
=IPMT(6%/4, 5, 20, 50000, 15000, 1)
```

**Result:** Calculates the interest portion of the 5th quarterly payment for a loan
of $50,000, repaid quarterly at 6% annual interest, with a desired future value of $15,000 and payments due at the
beginning of each period.

### 3. Annual Payment for Investment:

```excel
=IPMT(8%, 2, 10, -10000)
```

**Result:** Calculates the interest portion of the 2nd annual payment for an investment of $10,000 (negative value
indicates cash inflow from an investment), with 8% annual interest over 10 years.

## Notes:

- The **per** argument must be between `1` and `nper` or Excel will return a `#NUM!` error.
- Ensure that the **rate** and **nper** use the same period units. For example:
    - If payments are monthly, divide the annual interest rate by `12` and ensure **nper** reflects the total number of
      months.
    - For yearly payments, use the annual interest rate directly and adjust **nper** for the total number of years.
- The **fv** and **type** arguments are optional. If omitted, Excel assumes:
    - Future value (`fv`) is `0`.
    - Payments are due at the end of the period (`type = 0`).
- Positive and negative values for **pv** and **fv** represent cash inflows and outflows respectively.

## Applications:

- **Loan Amortization**: Separates principal and interest portions of loan payments for detailed financial tracking.
- **Investment Analysis**: Helps calculate the interest received for cash inflows during specific periods.
- **Cash Flow Forecasting**: Useful in understanding the interest expense or income over time in financial planning.

> **Tip:** Combine `IPMT` with other related financial functions like `PPMT` (Principal Payment) and `PMT` (Total
Payment) for comprehensive loan or investment analysis. Always check if your rate is consistent with your payment
frequency to avoid inaccuracies.