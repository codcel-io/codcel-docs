<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## XIRR Function

The `XIRR` function in Excel calculates the **internal rate of return (IRR)** for a series of cash flows that occur at
irregular intervals. It is particularly useful for financial analysis scenarios where cash flows are not evenly spaced,
such as investments or loans with unpredictable payments or returns.

### Key Features of XIRR:

- Suitable for cash flows occurring on irregular dates.
- Helps evaluate the profitability of investments or projects based on actual cash flow timing.
- Computes the unique annualized rate of return that aligns the present value of cash inflows and outflows to zero.

### Syntax:

```plaintext
XIRR(values, dates, [guess])
```

- **values**: A range of numbers representing the cash flows.
    - Positive values are inflows (e.g., revenues or returns).
    - Negative values are outflows (e.g., investments or costs).
    - The first cash flow (typically negative) should represent the initial investment.
- **dates**: A range of corresponding dates for each cash flow in the `values` array.
    - The number of dates must match the number of cash flows.
    - Dates must be entered in chronological order.
- **[guess]**: (Optional) An initial guess for the IRR. If omitted, Excel uses a default guess of `0.1` (10%).

### Examples:

1. **Basic Calculation**:
   `=XIRR({-5000, 1200, 1500, 3600, 2000}, {"2023-01-01", "2023-06-01", "2024-01-01", "2024-12-01", "2025-06-01"})`  
   Calculates the internal rate of return for an investment of $5,000, with cash inflows occurring at irregular
   intervals.  
   **Result**: `0.1634` (16.34% annualized IRR).

2. **Using a Guess**:
   `=XIRR({-8000, 2000, 4000, 5000}, {"2023-01-01", "2023-09-01", "2024-05-01", "2024-12-01"}, 0.2)`  
   Specifies an initial guess of 20% for the IRR.  
   **Result**: `0.2135` (21.35% annualized IRR).

### Notes:

- **Interpretation**: A higher XIRR indicates a more profitable investment or project. If the result is negative, it
  suggests the investment may result in a loss.
- **Error values**:
    - If `#NUM!` is returned, Excel couldn't find a solution. In this case, try modifying the `guess`.
    - Ensure all cash flows and dates are entered correctly; mismatched ranges will return `#VALUE!`.
- **Usage Tips**:
    - Typically, the first value in `values` (initial investment) is negative, representing a cash outflow.
    - Cash flows do not need to follow a fixed interval; the `dates` parameter allows for precise modeling of irregular
      timing.

### Calculation Explanation:

Internally, the `XIRR` function solves the equation for the IRR that makes the net present value (NPV) of all cash flows
equal to zero:

```plaintext
NPV = Σ [Cash Flow at i / (1 + IRR)^(Days(i) / 365)] = 0
```

Where:

- `Cash Flow at i` is the cash flow at a given time.
- `Days(i)` is the number of days since the start date.

> **Tips**:
> - Use `XIRR` when periodic intervals are inconsistent; for evenly spaced cash flows, consider using `IRR`.
> - Ensure dates represent accurate timing to reflect realistic investment outcomes.
> - The `guess` parameter can help Excel find a valid result, especially for complex cash flow patterns.