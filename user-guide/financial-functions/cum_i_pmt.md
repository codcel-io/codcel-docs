<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# CUMIPMT Function

The `CUMIPMT` function in Excel is used to calculate the **cumulative interest paid** on a loan or an investment over a
specific number of payment periods. This function is common in financial analysis to determine the total interest cost
for a given loan.

## Key Features of CUMIPMT:

- Calculates the **total interest** paid during a range of payment periods on a loan with fixed periodic payments and a
  constant interest rate.
- Useful for evaluating the cost of borrowing or the efficiency of loan repayment strategies.

## Syntax:

```plaintext
CUMIPMT(rate, nper, pv, start_period, end_period, type)
```

- **rate**: The interest rate for each period (annual rate divided by the number of periods per year).
- **nper**: The total number of payment periods for the loan.
- **pv**: The present value (principal or loan amount).
- **start_period**: The starting payment number for the calculation.
- **end_period**: The ending payment number for the calculation.
- **type**: Specifies when payments are due:
    - `0`: Payment at **end** of the period.
    - `1`: Payment at **beginning** of the period.

## How It Works:

1. Takes the fixed interest rate, loan term, initial amount, and range of payment periods to calculate the total
   interest paid.
2. Adds up the interest components from each period within the specified range.

## Examples:

### 1. Calculate Interest Paid Over the First Year:

A loan of $100,000 with a 5% annual interest rate, 10 years (120 monthly payments), and payments at the end of the
period.

```excel
=CUMIPMT(5%/12, 120, 100000, 1, 12, 0)
```

**Result:** The total interest paid over the first year of the loan.

### 2. Calculate Interest Paid Between Years 3 and 5:

For the same loan, sum total interest between months 25 and 60.

```excel
=CUMIPMT(5%/12, 120, 100000, 25, 60, 0)
```

**Result:** The interest paid during the third to fifth years of the loan.

### 3. Calculate Interest for Payments at the Beginning of the Period:

If the loan payments are made at the beginning of each period:

```excel
=CUMIPMT(5%/12, 120, 100000, 1, 12, 1)
```

**Result:** The total interest paid during the first year, but considering payments due at the start of each month.

## Notes:

- The **rate** must be adjusted to the periodic rate (e.g., annual rate divided by 12 for monthly payments).
- The **start_period** and **end_period** must be valid payment numbers (e.g., from 1 to the total number of periods),
  or Excel will return a `#NUM!` error.
- The loan terms must align across inputs (e.g., if payment periods are months, the interest rate and total periods must
  reflect monthly terms).
- If inputs are invalid or incomplete, Excel may return a `#VALUE!` error.

## Applications:

- **Loan Cost Analysis**: Helps quantify the interest expense over specific portions of a loan's life.
- **Financial Planning**: Useful for deciding repayment schedules or evaluating refinancing options.
- **Investment Analysis**: Applies to evaluating the cumulative interest cost for fixed-period investments or loans.

> **Tip:** Always use consistent units for periods and interest rates (e.g., monthly periods with a monthly interest
> rate).