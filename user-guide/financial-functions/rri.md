<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## RRI Function

The `RRI` function in Excel calculates the **equivalent interest rate** for an investment or savings that grows to a
specified future value over a given number of periods. It essentially determines the compound annual growth rate (CAGR)
required to reach a target value.

### Key Features of RRI:

- Computes the compound annual growth rate (CAGR) of an investment.
- Useful for estimating returns needed to reach a financial goal.
- A good tool for comparing investment growth rates over time.

### Syntax:

```plaintext
RRI(nper, pv, fv)
```

- **nper**: The total number of periods (or years) over which the investment will grow.
- **pv**: The present value (initial investment or starting amount).
- **fv**: The future value (desired investment amount or savings goal).

### Examples:

1. **Basic CAGR Calculation**:
   `=RRI(10, 10000, 20000)`  
   Calculates the annual growth rate needed to grow $10,000 to $20,000 over 10 years.  
   **Result**: `7.18%`

2. **Shorter Growth Period**:
   `=RRI(5, 5000, 10000)`  
   Determines the annual growth rate required to double an investment of $5,000 to $10,000 in 5 years.  
   **Result**: `14.87%`

3. **Larger Growth Requirement**:
   `=RRI(20, 50000, 200000)`  
   Calculates the annual growth rate to grow $50,000 to $200,000 over 20 years.  
   **Result**: `7.18%`

### Notes:

- **nper (number of periods)** should be entered as a numeric value (e.g., years, quarters, months, etc.), but ensure
  this aligns with the growth frequency expected for the outcome.
- The **pv (present value)** must always be a positive number greater than zero.
- The function assumes compound growth at a consistent rate.
- Returns a decimal number, which can be converted to a percentage by formatting the cell or multiplying by 100.

> **Tips**:
> - Use the `RRI` function to estimate the annual interest rate or growth rate required for achieving specific financial
    goals.
> - Combine this function with other Excel financial functions like `FV`, `PV`, or `NPER` for comprehensive investment
    analysis.
> - Be consistent with the time period definition for `nper` (e.g., years vs. months) to avoid incorrect results.