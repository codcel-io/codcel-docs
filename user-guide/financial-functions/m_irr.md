<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## MIRR Function

The `MIRR` function in Excel calculates the **Modified Internal Rate of Return** for a series of cash flows that occur
at regular intervals. Unlike the standard `IRR` function, which assumes a constant reinvestment rate, `MIRR` accounts
for separate financing and reinvestment rates, making it a more accurate representation of an investment's
profitability.

This function is particularly useful in financial analysis to evaluate project performance, investment profitability,
and capital budgeting when reinvestment of cash inflows occurs at a different rate from the cost of financing.

---

### Key Features of MIRR:

- Calculates a rate of return that incorporates both the cost of borrowing (financing rate) and the reinvestment rate.
- Useful for assessing projects with uneven cash flows and different financing/reinvestment conditions.
- Recognized as a more realistic measure of return compared to the traditional IRR.

---

### Syntax:

```plaintext
MIRR(values, finance_rate, reinvest_rate)
```

- **values**: An array or range of cells containing the series of cash flows.
    - Must include at least one negative value (outflows) and one positive value (inflows).
    - The order of cash flows matters, as they are assumed to occur in consecutive periods.
- **finance_rate**: The interest rate (cost) paid on cash outflows (financing rate).
- **reinvest_rate**: The interest rate received on cash inflows (reinvestment rate).

---

### Examples:

1. `=MIRR({-1000, 300, 500, 700}, 0.08, 0.10)`  
   Calculates the Modified Internal Rate of Return for an investment with an initial outflow
   of $1,000 and subsequent yearly inflows of $300, $500, and $700, assuming an 8% cost of financing and a 10%
   reinvestment rate.  
   **Result**: `12.13%` *(example value; actual result depends on calculation).*

2. `=MIRR(A1:A5, 0.05, 0.07)`  
   Computes the MIRR for a cash flow series stored in the range `A1:A5`, with a financing rate of 5% and a reinvestment
   rate of 7%.  
   **Result**: *(actual value depends on input data in `A1:A5`).*

3. `=MIRR({-50000, 20000, 15000, 10000, 25000}, 0.06, 0.08)`  
   Calculates the MIRR of a 5-period cash flow starting with an outflow of $50,000, adjusted for a 6% financing rate and
   8% reinvestment rate.  
   **Result**: `8.94%` *(example value).*

---

### Notes:

- The **values** array must include at least one negative cash flow (e.g., an investment or expenditure) and one
  positive cash flow (e.g., a return).
- If the **values** only contain positive or negative numbers, the function will return an error (`#DIV/0!`).
- Cash flow values are considered to occur at the end of each period.
- The **finance_rate** represents the borrowing cost of initial investments, while the **reinvest_rate** reflects the
  rate of return for reinvested cash flows.
- The MIRR is especially suitable for comparing projects with different cash flow structures.

> **Tip**: Use `MIRR` over `IRR` when cash inflows and reinvestment occur at rates different from the financing rate. It
provides a more conservative estimate of a project's profitability compared to IRR.