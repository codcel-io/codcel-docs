<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# CUMPRINC Function

The `CUMPRINC` function in Excel is used to calculate the **cumulative principal paid** on a loan or an investment over
a specific range of payment periods. It is commonly used in financial analysis to evaluate how much of the loan balance
has been paid off.

## Key Features of CUMPRINC:

- Calculates the **total principal portion** of payments made for a loan with fixed payments and a constant interest
  rate.
- Helpful in analyzing loan amortization schedules and understanding how loan repayments are reducing the outstanding
  principal.

## Syntax:

```plaintext
CUMPRINC(rate, nper, pv, start_period, end_period, type)
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

1. Takes the fixed interest rate, loan term, initial amount, and range of payment periods to calculate the total *
   *principal** portion of payments.
2. Accumulates the principal values of each payment within the specified range, ignoring the interest portion.

## Examples:

### 1. Calculate Principal Paid Over the First Year:

A loan of $100,000 with a 5% annual interest rate, 10 years (120 monthly payments), and payments at the end of the
period.

```excel
=CUMPRINC(5%/12, 120, 100000, 1, 12, 0)
```

**Result:** The total principal paid during the first year of the loan.

### 2. Calculate Principal Paid Between Years 3 and 5:

For the same loan, calculate the cumulative principal paid between months 25 and 60.

```excel
=CUMPRINC(5%/12, 120, 100000, 25, 60, 0)
```

**Result:** The total principal paid during years 3 to 5.

### 3. Calculate Principal Paid for Payments at the Beginning of the Period:

If the loan payments are made at the beginning of each period:

```excel
=CUMPRINC(5%/12, 120, 100000, 1, 12, 1)
```

**Result:** The total principal paid during the first year, considering payments due at the start of each month.

## Notes:

- The **rate** must be adjusted to reflect the period frequency (e.g., annual rate divided by 12 for monthly payments).
- The **start_period** and **end_period** must be valid payment numbers (e.g., between 1 and the total number of
  periods), or Excel will return a `#NUM!` error.
- The loan terms must align across inputs (e.g., if payment periods are months, the interest rate and total periods must
  reflect monthly terms).
- If inputs are invalid or incomplete, Excel may return a `#VALUE!` error.

## Applications:

- **Loan Repayment Analysis**: Helps borrowers understand how much of each repayment goes toward reducing the principal
  balance.
- **Financial Planning**: Useful for monitoring progress on loan repayment milestones.
- **Investment Analysis**: Evaluates how much equity has been built up over a specific time frame.

> **Tip:** Use the `CUMPRINC` function in combination with other functions like `CUMIPMT` for a full breakdown of loan
payments into principal and interest components.