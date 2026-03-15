<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## NPV Function

The `NPV` function in Excel calculates the **net present value** of an investment or project based on a series of cash
flows and a constant discount rate. It is widely used in financial and capital investment analyses to determine the
profitability or feasibility of an investment.

This function is particularly useful for comparing different investment opportunities or assessing the potential return
of a project by considering the time value of money.

---

### Key Features of NPV:

- Helps compute the present value of future cash flows discounted at a given rate.
- Best used when cash flows occur at regular intervals (e.g., monthly, quarterly, yearly).
- Assumes the first cash flow occurs at the end of the first period.
- Often combined with the `IRR` function to analyze investment returns comprehensively.

---

### Syntax:

```plaintext
NPV(rate, value1, [value2], ...)
```

- **rate**: The discount rate (or required rate of return) per period.
    - Must be provided as a decimal (e.g., 5% = 0.05).
    - Represents the time value of money or the desired return.
- **value1, [value2], ...**: Cash flows for each period.
    - These can be a range of cells or individual values.
    - Cash inflows should be entered as positive numbers, and cash outflows as negative numbers.

---

### Examples:

1. **Project with Annual Cash Flows**
   ```excel
   =NPV(0.08, 10000, 15000, 20000, 25000)
   ```  
   Calculates the net present value of a project with annual cash inflows of `$10,000`, `$15,000`, `$20,000`, and
   `$25,000` discounted at an annual rate of `8%`.  
   **Result**: `$55,818.12` *(example value).*

2. **Using a Range of Cells**
   ```excel
   =NPV(0.05, A1:A5)
   ```  
   Finds the NPV of cash flows listed in cells `A1` through `A5` with a `5%` discount rate.

3. **Mixed Cash Flow Direction**
   ```excel
   =NPV(0.1, -50000, 20000, 25000, 30000)
   ```  
   Computes the NPV of a project that starts with an initial investment of `-50,000` and generates annual cash inflows
   of `$20,000`, `$25,000`, and `$30,000`, discounted at a `10%` rate.  
   **Result**: `$11,337.22` *(example value).*

---

### Notes:

- The **NPV** function assumes cash flows occur **at the end of each period**. If a cash flow occurs at the beginning of
  a period (such as an initial investment), it should be added explicitly to the result:
  ```excel
  =NPV(rate, value1, value2, ...) + initial_investment
  ```
- If the discount rate is `0`, the NPV is equivalent to the simple sum of the cash flows.
- Negative NPV values indicate the project or investment is not profitable under the given conditions.

---

### Common Errors:

1. **`#NUM!`**: The discount rate provided is invalid (e.g., less than `-1`, or inappropriate periodic cash flow
   mismatches).
2. **`#VALUE!`**: Occurs when non-numeric inputs are provided for the cash flows or discount rate.

> **Tip**: Leverage `NPV` alongside other financial functions like `IRR` or `XNPV` for more robust investment analysis,
> especially for irregular cash flows or returns.

---