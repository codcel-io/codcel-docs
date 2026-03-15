<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# FV Function

The `FV` function in Excel calculates the **future value** of an investment based on periodic, constant payments and a
fixed interest rate. It is widely used for financial planning, enabling users to estimate the amount of money an
investment or savings account will grow to over time.

## Key Features of FV:

- Determines the future value of periodic payments or a single lump-sum investment.
- Helps in financial goal-setting by forecasting how savings or investments will grow.
- Useful for evaluating different investment or savings strategies.

## Syntax:

```plaintext
FV(rate, nper, pmt, [pv], [type])
```

### Arguments:

1. **rate**: The interest rate per period. For example:
    - For an annual interest rate of 6% with monthly payments, use `6%/12` or `0.06/12`.
2. **nper**: The total number of payment periods in the investment. For example:
    - For a 5-year investment with monthly payments, use `5*12`.
3. **pmt**: The payment made each period (negative for cash outflows such as deposits or investments). If omitted, it is
   assumed to be 0.
4. **[pv]** *(optional)*: The present value (initial lump-sum investment or loan amount). Default is `0`.
5. **[type]** *(optional)*: Indicates when payments are due:
    - `0` (or omitted): Payments are due at the end of the period.
    - `1`: Payments are due at the beginning of the period.

## How It Works:

1. The FV function uses the following formula to calculate the future value:

   ```plaintext
   FV = -(pv * (1 + rate)^nper + pmt * (1 + rate*type) * ((1 + rate)^nper - 1) / rate)
   ```

2. Here:
    - Positive results indicate money you will receive.
    - Negative values represent money paid (outflows).

## Examples:

### 1. Calculate Future Value of a Monthly Savings Plan:

```excel
=FV(5%/12, 60, -200, 0, 0)
```

**Result:** `$13,387.19`

This calculates the future value of saving $200 per month at an annual interest rate of 5% for 5 years.

---

### 2. Calculate Future Value with Both Present Value and Monthly Contributions:

```excel
=FV(4%/12, 120, -150, -5000, 0)
```

**Result:** `$27,292.15`

This calculates the future value of an initial investment of $5,000 and monthly contributions of $150 at an annual
interest rate of 4% over 10 years.

---

### 3. Future Value for Payments at the Beginning of Each Period:

```excel
=FV(6%/4, 8, -1000, 0, 1)
```

**Result:** `$8,525.62`

This calculates the future value of $1,000 quarterly payments for 2 years at an annual interest rate of 6%, where
payments are made at the beginning of the period.

---

### Notes:

- If **rate** is `0`, the formula simplifies to:

   ```plaintext
   FV = -(pv + (pmt * nper))
   ```

  This happens when there is no interest applied over time.
- Payments (**pmt**) and the present value (**pv**) should use consistent signs to indicate inflows (positive) or
  outflows (negative).

## Applications:

- **Retirement Planning**: Forecast the value of savings plans over a career span, with regular contributions.
- **Investment Growth**: Estimate the future value of lump-sum investments coupled with periodic contributions.
- **Loan Projections**: Understand how total loan or debt values evolve based on payment schedules and interest rates.

> **Tip:** For easier management of irregular payment schedules or changing rates, consider setting up an Excel table
with formulas to manually account for variations across periods.