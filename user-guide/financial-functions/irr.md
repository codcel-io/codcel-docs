<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# IRR Function

The `IRR` function in Excel calculates the **Internal Rate of Return (IRR)** for a series of cash flows occurring at
regular intervals. The IRR is the discount rate at which the **Net Present Value (NPV)** of the cash flows equals zero.
It is frequently used in financial analysis for evaluating investment opportunities.

## Key Features of IRR:

- Determines the break-even discount rate for a project or investment.
- Assumes cash flows occur at equal time intervals.
- Supports an optional **guess** argument to provide an initial estimate of the IRR.

## Syntax:

```plaintext
IRR(values, [guess])
```

### Arguments:

- **values**: An array or range of cells containing the cash flows.
    - It must include at least one negative value (representing the initial investment) and one positive value (
      indicating returns).
    - The order of the cash flows matters, as it assumes they occur sequentially.
- **guess**: (Optional) Your estimate for the IRR.
    - If omitted, Excel assumes a default value of 0.1 (10%).
    - Including a guess can improve calculation accuracy when the cash flows are irregular or produce multiple IRRs.

## How It Works:

1. The IRR function calculates the discount rate that, when applied to the cash flows, results in an NPV of 0.
2. Internally, Excel uses an iterative process to find the rate, starting with the **guess** if provided.
3. If the function does not converge to a solution, it returns the `#NUM!` error.

## Examples:

### 1. Basic IRR Calculation:

```excel
=IRR(A1:A5)
```

Where the range `A1:A5` includes the following cash flows:

- Initial investment: `-1000`
- Returns: `200, 300, 400, 500`

**Result:** `14.49%`

This calculates the internal rate of return based on the series of cash flows.

---

### 2. Specifying a Guess:

```excel
=IRR(B1:B6, 0.15)
```

Where the range `B1:B6` includes the following cash flows:

- Initial investment: `-5000`
- Returns: `1000, 1500, 2000, 2500, 3000`

**Result:** `18.86%`

This calculates the IRR using an initial guess of `15%`, ensuring faster convergence or resolving multiple IRR cases.

---

### 3. Cash Flows with Uneven Timing:

For cash flows with irregular timing, use the **XIRR** function instead of `IRR`. For example:

```excel
=XIRR(C1:C5, D1:D5)
```

Where `C1:C5` contains cash flows and `D1:D5` contains their corresponding dates.

---

## Notes:

- If the **values** array does not include at least one negative and one positive cash flow, the function returns the
  `#NUM!` error.
- The IRR may have multiple solutions or no solution, depending on the pattern of cash flows.
- In cases of ambiguity or calculation challenges, try providing a reasonable **guess** to guide the function.

## Applications:

- **Investment Analysis**: Assess whether an investment achieves a desired rate of return.
- **Capital Budgeting**: Evaluate the IRR of various projects to prioritize investments.
- **Business Decision-Making**: Compare the profitability of multiple cash flow streams.

> **Tip:** Use `IRR` together with `NPV` to calculate and validate investment decisions. For example, find the IRR
> first, then confirm that the NPV is zero at that rate.