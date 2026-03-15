<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# FVSCHEDULE Function

The `FVSCHEDULE` function in Excel calculates the **future value** of an initial investment based on a series of
specified interest rates (the schedule). Unlike the `FV` function, which assumes a constant rate for all periods,
`FVSCHEDULE` allows for variable rates, making it useful for scenarios where interest rates change over time.

## Key Features of FVSCHEDULE:

- Calculates future value when interest rates vary across periods.
- Handles irregular rate schedules, providing flexibility for forecasting in non-standard financial scenarios.
- Useful for modeling investments or savings with fluctuating interest rates.

## Syntax:

```plaintext
FVSCHEDULE(principal, schedule)
```

### Arguments:

1. **principal**: The initial amount of the investment or capital (can be positive or negative based on the context).
2. **schedule**: An array (or range) of interest rates applied for each period. The array can contain positive or
   negative rate values.

### How It Works:

1. The formula applies each rate in the schedule successively to the value from the previous period:

   ```plaintext
   Future Value = Principal * (1 + Rate1) * (1 + Rate2) * ... * (1 + RateN)
   ```

2. Each interest rate in the **schedule** is compounded sequentially, adjusting the investment's balance over time.

## Examples:

### 1. Calculate the Future Value of an Investment with Varying Annual Rates:

```excel
=FVSCHEDULE(1000, {5%, 6%, 4%})
```

**Result:** `$1157.04`

This calculates the future value of an initial investment of $1,000 after three years, where the annual interest rates
are 5% for the first year, 6% for the second year, and 4% for the third year.

---

### 2. Include Negative Rates to Represent Losses:

```excel
=FVSCHEDULE(5000, {8%, -2%, 5%})
```

**Result:** `$5632.80`

This calculates the future value of $5,000 considering an 8% gain in the first year, a -2% loss in the second year, and
a 5% gain in the third year.

---

### 3. Use a Cell Range for the Schedule:

If interest rates for four years are stored in cells `B1:B4`, you can calculate the future value like this:

```excel
=FVSCHEDULE(2000, B1:B4)
```

The function dynamically references the range `B1:B4` for rates. If the rates are 3%, 4%, 5%, and -2%, the result will
reflect four years of compounding with those rates.

---

### Notes:

- The **principal** is adjusted based on the compound growth (or decay) for each rate in the schedule.
- Rates must be expressed in decimal or percentage format (e.g., `5%` or `0.05`).
- A **negative rate** results in a reduction of principal for that period (e.g., a -2% rate decreases the value).

---

## Applications:

- **Variable Interest Investments**: Model investments where interest rates fluctuate annually, quarterly, or monthly.
- **Economic Forecasting**: Simulate how changes in economic conditions (e.g., inflation, market interest rates) affect
  an investment.
- **Scenario Analysis**: Test various rate schedules to project possible future outcomes for financial planning.

> **Tip:** Always double-check that the provided schedule matches the correct periods for accurate results. For
> irregular periods, consider restructuring the schedule data.