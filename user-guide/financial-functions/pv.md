<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PV Function

The `PV` function in Excel calculates the **present value** of an investment or loan, based on constant payments and a
constant interest rate. This function is useful for determining the current worth of a series of future payments or
incomes.

### Key Features of PV:

- Computes the present value of cash flows that occur in equal intervals, such as loan payments or annuities.
- Useful for evaluating loans, mortgages, or investment opportunities.
- Assumes consistent periodic payments and a fixed interest rate over the duration of the investment or loan.

### Syntax:

```plaintext
PV(rate, nper, pmt, [fv], [type])
```

- **rate**: The interest rate per period. For example, for a 5% annual interest rate, use `0.05` (or divide by `12` for
  monthly interest rates: `0.05/12`).
- **nper**: The total number of payment periods for the investment or loan.
- **pmt**: The payment made in each period. This value should include both principal and interest and is generally
  entered as a negative value (representing cash outflow).
- **[fv]** *(optional)*: The future value, or cash balance desired after the final payment. Defaults to `0` if omitted.
- **[type]** *(optional)*: Specifies when payments are made:
    - `0` (default) for payments made at the **end** of the period.
    - `1` for payments made at the **beginning** of the period.

### Examples:

1. **Loan Present Value**:
   `=PV(0.05/12, 60, -377.42)`  
   Calculates the loan amount (present value) based on monthly payments of $377.42 at a 5% annual interest over 5
   years.  
   **Result**: `$20,000`.

2. **Investment Present Value**:
   `=PV(0.04/4, 8*4, -500, 10000)`  
   Evaluates the present value of an investment with quarterly payments
   of $500 for 8 years at 4% annual interest, with a desired future value of $10,000.  
   **Result**: `-$25,242.89` (negative indicates initial cash outflow).

3. **Without Payments**:
   `=PV(0.06/12, 24, 0, 10000)`  
   Determines the present value of receiving $10,000 after 2 years, assuming a 6% annual interest rate.  
   **Result**: `$9,432.06`.

### Notes:

- The **rate** and **nper** must align in terms of time unit. For example:
    - If **rate** is the monthly interest rate, **nper** must represent the number of months.
    - If **rate** is the annual interest rate, **nper** must represent years.
- The **pmt** value:
    - Should be negative for outgoing payments (e.g., for loans).
    - May be `0` for scenarios where the future value is desired without regular payments (such as a lump sum).
- The result is returned as a negative value to indicate a cash outflow. Use `ABS()` to show this as a positive value if
  desired.

> **Tips**:
> - Use the `PV` function to compare the current worth of different financial scenarios or investment options.
> - Combine with other functions like `FV` (Future Value) for full financial analysis.
> - Double-check units for interest rate and payment frequency to ensure consistent results.