<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## PDURATION Function

The `PDURATION` function in Excel calculates the **number of periods** required for an investment to grow to a specified
future value at a constant interest rate. This function is useful for financial planning, investment analysis, and
understanding the time required to achieve financial goals.

### Key Features of PDURATION:

- Computes the number of periods required for an investment to grow to a target value based on a constant growth rate.
- Useful in scenarios such as savings growth, retirement planning, or financial goal planning.
- Eliminates the need for iterative calculations by directly providing the result.

### Syntax:

```plaintext
PDURATION(rate, present_value, future_value)
```

- **rate**: The interest rate per period (expressed as a decimal).
- **present_value**: The current value of the investment.
- **future_value**: The desired future value of the investment.

### Examples:

1. `=PDURATION(0.05, 1000, 2000)`  
   Calculates the number of periods required for an investment of $1,000 to grow to $2,000 at an annual interest rate of
   5%.  
   **Result**: `14.21` periods.

2. `=PDURATION(0.08, 5000, 10000)`  
   Computes the number of periods required for $5,000 to double to $10,000 at an 8% annual growth rate.  
   **Result**: `9.01` periods.

3. `=PDURATION(0.03, 15000, 20000)`  
   Calculates the time needed for $15,000 to grow to $20,000 at a growth rate of 3% per year.  
   **Result**: `9.56` periods.

### Notes:

- The **rate** must be provided in a format consistent with the growth period. For example, if the goal is for monthly
  growth, use the monthly interest rate.
- Both **present_value** and **future_value** must be positive numbers; the function assumes positive growth.
- The function returns the number of periods as a decimal, which can represent fractional periods (e.g., portions of a
  year for annual rates).

> **Tips**:
> - Use `PDURATION` in conjunction with other financial functions like `FV` (Future Value) or `PV` (Present Value) for a
    comprehensive plan.
> - Ensure the rate and period frequency are aligned (e.g., annual rates for years, monthly rates for months) to get
    accurate results.