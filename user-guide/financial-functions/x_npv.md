<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## XNPV Function

The `XNPV` function in Excel calculates the **net present value (NPV)** for a series of cash flows that occur at
irregular intervals, based on a specified discount rate. It is particularly useful for evaluating the profitability of
investments or projects where cash flows and timing are inconsistent.

### Key Features of XNPV:

- Suitable for cash flows occurring on irregular dates.
- Accounts for the time value of money by discounting cash flows based on actual dates.
- Provides a more accurate NPV calculation for projects with unpredictable cash flow timings.

### Syntax:

```plaintext
XNPV(rate, values, dates)
```

- **rate**: The discount rate used to calculate the present value of cash flows.
    - Typically expressed as an annual rate (e.g., `0.1` for 10%).
- **values**: A range of cash flow amounts (positive or negative).
    - Positive values are inflows (e.g., profits).
    - Negative values are outflows (e.g., costs or investments).
- **dates**: A range of corresponding dates for each cash flow.
    - The number of dates must match the number of cash flows in `values`.
    - Dates must be in chronological order.

### Examples:

1. **Basic Calculation**:
   `=XNPV(0.1, {-5000, 1200, 1500, 3600, 2000}, {"2023-01-01", "2023-06-01", "2024-01-01", "2024-12-01", "2025-06-01"})`  
   Calculates the net present value of investing $5,000 with cash inflows on irregular dates and a discount rate of
   10%.  
   **Result**: `534.73`

2. **Alternative Scenario**:
   `=XNPV(0.08, {-10000, 3000, 4000, 5000}, {"2023-01-01", "2023-06-01", "2024-01-01", "2025-01-01"})`  
   Computes the NPV for a project with an 8% discount rate and varied cash flows.  
   **Result**: `729.14`

### Notes:

- **Interpretation**: A positive XNPV result indicates a profitable investment (in terms of present value). A negative
  value implies the investment may result in a loss.
- **Error values**:
    - If `#NUM!` occurs, check for inconsistent or invalid dates.
    - Mismatched ranges for `values` and `dates` will return `#VALUE!`.
- **Usage Tips**:
    - Ensure that the first cash flow (usually negative) represents the initial investment cost.
    - Double-check that dates and cash flow amounts align correctly to avoid calculation errors.
    - The discount rate significantly affects the NPV result; consider using precise and realistic rate assumptions.

### Calculation Explanation:

The `XNPV` function calculates the present value of each cash flow, discounted to the start date, and sums these values.
The formula for net present value is as follows:

```plaintext
XNPV = Σ [Cash Flow at i / (1 + rate)^(Days(i) / 365)]
```

Where:

- `Cash Flow at i` is the cash amount at a specific date.
- `rate` is the discount rate.
- `Days(i)` is the number of days between the start date and the date of the cash flow `i`.

> **Comparison to NPV**:
> - Use `XNPV` when cash flows occur at irregular intervals (exact dates), as it considers the actual timing of each
    transaction.
> - The `NPV` function is limited to cash flows occurring evenly over regular intervals.