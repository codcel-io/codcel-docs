<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FORECAST.ETS.CONFINT Function

The `FORECAST.ETS.CONFINT` function in Excel returns a **confidence interval** for a forecast value at a specified
target date, using the **Exponential Smoothing (ETS)** algorithm. This function quantifies the uncertainty of a
`FORECAST.ETS` prediction, giving you the range within which the actual future value is likely to fall.

### Key Features of FORECAST.ETS.CONFINT:

- Returns the width of the confidence interval (margin of error) for an ETS forecast at a given confidence level.
- Uses the same **exponential triple smoothing** model as `FORECAST.ETS`.
- Automatically detects **seasonal patterns** within the data.
- Allows you to specify a custom confidence level (default is 95%).
- Supports the same data completion and aggregation options as `FORECAST.ETS`.

### Syntax:

```plaintext
FORECAST.ETS.CONFINT(target_date, values, timeline, [confidence_level], [seasonality], [data_completion], [aggregation])
```

#### Arguments:

1. **target_date** *(required)*:
   The date (or time) for which you want to calculate the confidence interval of the forecast.
   *Must be a numeric value or valid date/time format.*

2. **values** *(required)*:
   The dependent data set (historical data) containing the values used for the forecast.

3. **timeline** *(required)*:
   The independent set of dates or time periods corresponding to the `values`.
   *The timeline must have consistent steps (e.g., daily, monthly intervals) and cannot contain duplicates.*

4. **confidence_level** *(optional)*:
   A numeric value between 0 and 1 (exclusive) specifying the confidence level for the interval. Default is `0.95`
   (95% confidence).
    - `0.90`: 90% confidence interval (narrower).
    - `0.95`: 95% confidence interval (default).
    - `0.99`: 99% confidence interval (wider).

5. **seasonality** *(optional)*:
   A numeric value to specify the length of the seasonal pattern. Options:
    - `0`: No seasonality (produces a non-seasonal forecast).
    - `1`: Automatically detect seasonality (default).
    - A positive integer to manually define the season length (e.g., `12` for monthly data with yearly seasonality).

6. **data_completion** *(optional)*:
   Specifies how to handle missing data points:
    - `0`: Missing data treated as zero.
    - `1`: (Default) Missing data completed using the average of neighboring points.

7. **aggregation** *(optional)*:
   Controls how duplicate timestamps in the timeline are aggregated. Default is `AVERAGE`.
   Options include `SUM`, `COUNT`, `MEDIAN`, etc.

---

### How It Works:

The `FORECAST.ETS.CONFINT` function calculates the confidence interval around the forecast produced by
`FORECAST.ETS`. It uses the same underlying **exponential triple smoothing** model but returns the half-width of the
confidence interval rather than the point forecast itself.

The confidence interval is computed from the standard error of the forecast residuals and the number of steps ahead
being predicted. The further into the future the target date is, the wider the confidence interval becomes, reflecting
increasing uncertainty.

To construct the full forecast range, combine it with `FORECAST.ETS`:

```plaintext
Lower bound = FORECAST.ETS(...) - FORECAST.ETS.CONFINT(...)
Upper bound = FORECAST.ETS(...) + FORECAST.ETS.CONFINT(...)
```

---

### Examples:

1. **95% Confidence Interval for Monthly Sales:**

   Assume the following:
    - Sales data is in `B2:B13` (monthly sales).
    - Corresponding months are in `A2:A13`.
    - You want the confidence interval for the forecast of the month in cell `A14`.

   Use the formula:

   ```excel
   =FORECAST.ETS.CONFINT(A14, B2:B13, A2:A13)
   ```

   This returns the margin of error at the default 95% confidence level with automatic seasonality detection.

2. **99% Confidence Interval with Explicit Seasonality:**

   To calculate a wider (99%) confidence interval with a 12-month seasonal cycle:

   ```excel
   =FORECAST.ETS.CONFINT(A14, B2:B13, A2:A13, 0.99, 12)
   ```

3. **Building a Forecast Range:**

   To display the forecast with upper and lower bounds:

   ```excel
   Forecast:    =FORECAST.ETS(A14, B2:B13, A2:A13)
   Lower bound: =FORECAST.ETS(A14, B2:B13, A2:A13) - FORECAST.ETS.CONFINT(A14, B2:B13, A2:A13)
   Upper bound: =FORECAST.ETS(A14, B2:B13, A2:A13) + FORECAST.ETS.CONFINT(A14, B2:B13, A2:A13)
   ```

4. **90% Confidence Interval with Missing Data Handling:**

   If you want a 90% confidence interval and missing values in `B2:B13` should be treated as `0`:

   ```excel
   =FORECAST.ETS.CONFINT(A14, B2:B13, A2:A13, 0.90, 1, 0)
   ```

5. **Confidence Interval with Aggregated Duplicates:**

   In scenarios where the timeline has duplicate entries, use aggregation:

   ```excel
   =FORECAST.ETS.CONFINT(A14, C2:C50, D2:D50, 0.95, 1, 1, "SUM")
   ```

   This sums up duplicate values in `D2:D50` before calculating the confidence interval.

---

# FORECAST.ETS.CONFINT — Excel Compatibility Notes

This document describes how Codcel's `FORECAST.ETS.CONFINT` implementation compares to Microsoft Excel, including what matches exactly and where to expect differences.

## Summary

| Scenario | Match with Excel | Typical Difference |
|----------|------------------|--------------------|
| Seasonal quarterly, perfect-fit data (period 4) | Exact | 0 |
| Seasonal monthly, perfect-fit data (period 12) | Exact | < 1e-13 |
| Seasonal with general data | Approximate | Varies |
| Non-seasonal monthly, 1 step ahead | Close | 0.4 – 0.5% |
| Non-seasonal monthly, multi-step ahead | Close | 0.4 – 0.9% |
| Non-seasonal quarterly, 1 step ahead | Close | 0.3 – 0.4% |
| Quarterly with non-standard period (e.g. seasonality=2) | Approximate | 3% |

## What Matches Excel Exactly

### Seasonal with Perfect-Fit Data

When the seasonal ETS model achieves a perfect fit on the training data (e.g. a repeating pattern with linear trend), both Codcel and Excel converge to the same smoothing parameters and produce near-zero residual variance. In this case, `FORECAST.ETS.CONFINT` returns values that match Excel to within floating-point precision.

**Examples:**
- Quarterly data with `seasonality=4` at 95% confidence → Excel: **0.0**, Codcel: **0.0**
- Monthly data with `seasonality=12` at 95% confidence → Excel: **2.274e-14**, Codcel: **2.274e-14**

These near-zero values reflect that the seasonal ETS model fits the test data almost perfectly, leaving negligible residual variance.

**Note:** For general data where the fit is imperfect, Codcel's CMLE optimizer may find different smoothing parameters than Excel, producing different confidence intervals. See "Seasonal with General Data" below.

### Supported Parameters

All seven parameters of `FORECAST.ETS.CONFINT` are implemented:

| Parameter | Support |
|-----------|---------|
| `target_date` | Full support |
| `values` | Full support |
| `timeline` | Full support |
| `confidence_level` | Full support (default 0.95, range (0, 1)) |
| `seasonality` | 0 (none), 1 (auto-detect), or explicit period |
| `data_completion` | 0 (fill zeros) or 1 (interpolate, default) |
| `aggregation` | 1–7 (average, count, counta, max, median, min, sum) |

### Data Completion and Aggregation

Tests with `data_completion=0`, `data_completion=1`, and various aggregation modes all match Excel exactly for seasonal mode with perfect-fit data.

## Where Differences Occur

### Seasonal with General Data

For data that does not produce a perfect fit, Codcel's concentrated MLE optimizer may find different smoothing parameters than Excel's proprietary algorithm. Since the confidence interval depends on the fitted model's residual variance, different parameters lead to different intervals.

The magnitude of the difference depends on the data and seasonal period. Standard periods (4, 12) tend to produce smaller differences than non-standard periods (2, 3, 6).

### Non-Seasonal Monthly Data

When monthly data is used without seasonality (either `seasonality=0` or auto-detection finds no seasonal pattern due to insufficient cycles), differences range from 0.4% to 0.9%.

| Test Case | Confidence | Steps Ahead | Excel | Codcel | Difference |
|-----------|-----------|-------------|-------|--------|------------|
| basic_mon | 95% | 1 | 8.5620 | 8.5245 | −0.44% |
| mon_9_0 | 90% | 1 | 7.1854 | 7.1540 | −0.44% |
| mon_9_5 | 95% | 1 | 8.5620 | 8.5245 | −0.44% |
| mon_9_9 | 99% | 1 | 11.2523 | 11.2031 | −0.44% |
| mon_7_5 | 75% | 1 | 5.0252 | 5.0032 | −0.44% |
| mon_5_0 | 50% | 1 | 2.9465 | 2.9336 | −0.44% |
| mon_2_ahead | 95% | 2 | 12.1024 | 12.0555 | −0.39% |
| mon_2_ahead_9_0 | 90% | 2 | 10.1566 | 10.1173 | −0.39% |
| mon_jun_2_3 | 95% | 6 | 20.9899 | 20.8807 | −0.52% |
| mon_jul_2_3 | 95% | 7 | 22.6820 | 22.5538 | −0.57% |
| mon_far_fut | 95% | 13 | 30.9990 | 30.7356 | −0.85% |
| mon_far_fut_9_9 | 99% | 13 | 40.7396 | 40.3935 | −0.85% |

**Key observations:**
- The relative difference is consistent across confidence levels (always ~0.44% at 1-step)
- The difference grows slightly with forecast horizon (0.44% at 1-step → 0.85% at 13-steps)
- Codcel consistently produces slightly narrower intervals than Excel

### Non-Seasonal Quarterly Data

| Test Case | Confidence | Excel | Codcel | Difference |
|-----------|-----------|-------|--------|------------|
| qtr_seas_none | 95% | 25.0703 | 25.1547 | +0.34% |
| qtr_n_s_9_0 | 90% | 21.0396 | 21.1105 | +0.34% |
| qtr_n_s_5_0 | 50% | 8.6275 | 8.6566 | +0.34% |
| qtr_n_s_9_9 | 99% | 32.9479 | 33.0588 | +0.34% |

**Key observations:**
- The relative difference is very consistent at 0.34% across all confidence levels
- Codcel produces slightly wider intervals than Excel for quarterly data (opposite direction from monthly)

### Quarterly with Non-Standard Seasonality

| Test Case | Confidence | Excel | Codcel | Difference |
|-----------|-----------|-------|--------|------------|
| qtr_seas_2 | 95% | 24.9037 | 25.6630 | +3.0% |

This is the largest outlier. Non-standard seasonal periods (e.g. `seasonality=2` on quarterly data) stress the optimizer differently and may find different local minima.

## Why Differences Occur

### Excel's Proprietary Algorithm

Excel's `FORECAST.ETS.CONFINT` uses an undocumented, proprietary algorithm for computing prediction intervals. This has been confirmed by multiple independent sources:

- **Edward Bodmer** (Excel financial modelling expert) has documented that Excel's ETS confidence interval calculation does not match any published statistical formula
- **ExcelForum** users have been unable to reverse-engineer the exact formula
- **LibreOffice Calc** does not implement `FORECAST.ETS.CONFINT` at all
- **Python's statsmodels** produces different results from Excel for the same data

No open-source implementation has been able to replicate Excel's CONFINT values exactly.

### Codcel's Approach

Codcel uses a hybrid approach based on established statistical theory:

**For seasonal data (ETS):** Monte Carlo simulation with 1000 scenarios using the fitted ETS model parameters. A deterministic PRNG seeded from the data ensures reproducible results. The smoothing parameters are obtained from Nelder-Mead with concentrated MLE (innovations form). When the model achieves a perfect fit, the residual variance is near-zero and the simulation matches Excel exactly. For imperfect fits, different smoothing parameters from the optimizer can lead to different residual variances and thus different intervals.

**For non-seasonal data (EDS):** The Hyndman ETS(A,A,N) analytical prediction interval formula:

```
PI = z × σ × √(Σ c_j²)
```

where:
- `z = NORM.S.INV((1 + confidence_level) / 2)` is the normal quantile
- `σ` is the estimated residual standard deviation
- `c_0 = 1`, `c_j = α + j × β` for j ≥ 1 (Hyndman step factors)
- α, β are the innovations-form smoothing parameters from Nelder-Mead MLE

The variance estimator uses `SSE / (n - 4)` degrees-of-freedom correction (4 estimated parameters: α, β, l₀, b₀).

When the optimizer finds boundary parameters (α + β > 1), the code falls back to the MSSD/2 estimator (Mean Squared Successive Differences / 2) with random-walk step factors `√h`, which is the natural variance estimator for integrated/random-walk data.

**Reference:** Hyndman, Koehler, Ord & Snyder, *Forecasting with Exponential Smoothing: The State Space Approach*, Table 6.3.

### Source of the ~0.4% Monthly Difference

The 0.44% difference on monthly 1-step predictions traces to the variance estimator. Our concentrated MLE with MSSD/2 fallback gives `σ² = 18.92` for the monthly test data, while Excel's proprietary method implies `σ² ≈ 19.08`. The smoothing parameters and point forecasts are identical — only the variance estimate differs slightly.

### Source of the ~0.3% Quarterly Difference

For quarterly data, the Nelder-Mead optimizer finds near-zero smoothing parameters (α ≈ 0, β ≈ 0), equivalent to OLS linear regression. The `SSE / (n - 4)` degrees-of-freedom correction gives a variance estimate that is 0.34% higher than Excel's implied value.

## Technical Details

### Algorithm Selection

| Condition | Optimizer | Variance Estimator | Step Factors |
|-----------|-----------|-------------------|--------------|
| Seasonal (ETS) | Nelder-Mead with concentrated MLE | Monte Carlo simulation | N/A (simulated) |
| Non-seasonal, α + β > 1 | Nelder-Mead MLE | MSSD/2 = Σd²/(2n) | √h (random walk) |
| Non-seasonal, α + β ≈ 0 | Nelder-Mead MLE | SSE/(n−4) | √h (OLS-like growth) |
| Non-seasonal, 0 < α + β ≤ 1 | Nelder-Mead MLE | SSE/(n−4) | Hyndman c_j² sum |

### Parameter Naming Convention

| Codcel | Hyndman | Role |
|-------------------|---------|------|
| `alpha` | α | Level smoothing |
| `gamma` | β | Trend smoothing |
| `beta` | γ | Seasonal smoothing |

### Error Conditions

The following match Excel's behaviour:
- Target date within data range → returns `#NUM!` error
- `confidence_level` ≤ 0 or ≥ 1 → returns `#NUM!` error
- Mismatched array lengths → returns `#N/A` error
- Insufficient data points → returns `#VALUE!` error

## Validation Summary

- All generated integration tests pass
- Seasonal tests with perfect-fit data match Excel exactly
- Seasonal tests with general data are close to Excel; differences reflect different optimizer local minima
- Non-seasonal tests show small, consistent percentage differences documented above


### Applications:

- **Sales Projections:** Quantify the uncertainty around seasonal sales forecasts to plan inventory buffers.
- **Financial Planning:** Provide upper and lower revenue bounds for budgeting and risk assessment.
- **Energy Demand Forecasting:** Establish confidence bands around projected energy consumption for capacity planning.
- **Supply Chain Management:** Determine safety stock levels based on forecast uncertainty.

> **Tip:** Pair `FORECAST.ETS.CONFINT` with `FORECAST.ETS` to present forecasts as ranges rather than single values.
> This gives stakeholders a clearer picture of potential outcomes and helps with risk-based decision making. For
> simpler linear forecasting without seasonality, consider `FORECAST.LINEAR` instead.