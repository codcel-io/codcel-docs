<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FORECAST.ETS.STAT Function

The `FORECAST.ETS.STAT` function in Excel returns a statistical value related to the **Exponential Smoothing (ETS)**
forecast model for a given time series. This function provides access to the internal model parameters and goodness-of-fit
metrics used by `FORECAST.ETS`, making it useful for evaluating forecast quality and understanding model behaviour.

### Key Features of FORECAST.ETS.STAT:

- Returns a single statistical metric from the fitted ETS model based on the `stat_type` argument.
- Uses the same **exponential triple smoothing** algorithm as `FORECAST.ETS`.
- Provides access to smoothing parameters (alpha, beta, gamma), error metrics (MASE, SMAPE, MAE, RMSE), and step size.
- Supports the same data completion and aggregation options as `FORECAST.ETS`.

### Syntax:

```plaintext
FORECAST.ETS.STAT(values, timeline, stat_type, [seasonality], [data_completion], [aggregation])
```

#### Arguments:

1. **values** *(required)*:
   The dependent data set (historical data) containing the values used for the forecast model.

2. **timeline** *(required)*:
   The independent set of dates or time periods corresponding to the `values`.
   *The timeline must have consistent steps (e.g., daily, monthly intervals) and cannot contain duplicates.*

3. **stat_type** *(required)*:
   An integer from 1 to 8 specifying which statistic to return:

   | stat_type | Statistic | Description |
   |-----------|-----------|-------------|
   | 1 | Alpha (level) | Smoothing parameter for the level component (0 to 1). |
   | 2 | Beta (trend) | Smoothing parameter for the trend component (0 to 1). |
   | 3 | Gamma (seasonal) | Smoothing parameter for the seasonal component (0 to 1). |
   | 4 | MASE | Mean Absolute Scaled Error — a scale-independent error measure. |
   | 5 | SMAPE | Symmetric Mean Absolute Percentage Error (0 to 1). |
   | 6 | MAE | Mean Absolute Error — average of absolute forecast residuals. |
   | 7 | RMSE | Root Mean Squared Error — square root of mean squared residuals. |
   | 8 | Step size | The detected time step size between data points. |

4. **seasonality** *(optional)*:
   A numeric value to specify the length of the seasonal pattern. Options:
    - `0`: No seasonality (produces a non-seasonal model).
    - `1`: Automatically detect seasonality (default).
    - A positive integer to manually define the season length (e.g., `12` for monthly data with yearly seasonality).

5. **data_completion** *(optional)*:
   Specifies how to handle missing data points:
    - `0`: Missing data treated as zero.
    - `1`: (Default) Missing data completed using the average of neighboring points.

6. **aggregation** *(optional)*:
   Controls how duplicate timestamps in the timeline are aggregated. Default is `AVERAGE`.
   Options include `SUM`, `COUNT`, `MEDIAN`, etc.

---

### How It Works:

The `FORECAST.ETS.STAT` function fits the same **exponential triple smoothing** model as `FORECAST.ETS` to the
provided data and then extracts a specific statistic from the fitted model. Rather than returning a forecast value,
it returns information about the model itself.

The smoothing parameters (alpha, beta, gamma) control how quickly the model adapts to changes:
- **Alpha (level):** Higher values mean the model responds quickly to level changes.
- **Beta (trend):** Higher values mean the model responds quickly to trend changes.
- **Gamma (seasonal):** Higher values mean the model responds quickly to changes in the seasonal pattern.

The error metrics (MASE, SMAPE, MAE, RMSE) measure how well the model fits the historical data:
- **MASE < 1:** The model forecasts better than a naive (random walk) forecast.
- **SMAPE** is bounded between 0 and 1, making it easy to interpret as a percentage.
- **MAE** and **RMSE** are in the same units as the original data.

The **step size** (stat_type 8) returns the uniform time interval between consecutive data points (e.g., 1 for daily,
30–31 for monthly, 90–92 for quarterly), useful for verifying that the timeline is interpreted correctly.

---

### Examples:

1. **Retrieving the Alpha (Level) Smoothing Parameter:**

   Assume the following:
    - Sales data is in `B2:B25` (24 months of monthly sales).
    - Corresponding months are in `A2:A25`.

   Use the formula:

   ```excel
   =FORECAST.ETS.STAT(B2:B25, A2:A25, 1)
   ```

   This returns the alpha smoothing parameter for the level component of the fitted ETS model.

2. **Checking the MASE (Mean Absolute Scaled Error):**

   To evaluate model quality:

   ```excel
   =FORECAST.ETS.STAT(B2:B25, A2:A25, 4)
   ```

   A MASE value less than 1 indicates the ETS model forecasts better than a naive approach.

3. **Retrieving RMSE with Explicit Seasonality:**

   To get the RMSE using a 12-month seasonal cycle:

   ```excel
   =FORECAST.ETS.STAT(B2:B25, A2:A25, 7, 12)
   ```

4. **Comparing All Smoothing Parameters:**

   You can place these in adjacent cells to see all three smoothing parameters at once:

   ```excel
   Alpha: =FORECAST.ETS.STAT(B2:B25, A2:A25, 1)
   Beta:  =FORECAST.ETS.STAT(B2:B25, A2:A25, 2)
   Gamma: =FORECAST.ETS.STAT(B2:B25, A2:A25, 3)
   ```

5. **Non-Seasonal Model Statistics:**

   To retrieve the MAE for a non-seasonal model:

   ```excel
   =FORECAST.ETS.STAT(B2:B25, A2:A25, 6, 0)
   ```

   When `seasonality=0`, the gamma (stat_type 3) parameter is not applicable and returns `0`.

6. **Checking the Detected Step Size:**

   To verify how the timeline is interpreted:

   ```excel
   =FORECAST.ETS.STAT(B2:B25, A2:A25, 8)
   ```

   For monthly data, this typically returns a value around 30 (days between data points).


# FORECAST.ETS.STAT — Excel Compatibility Notes

This document describes how Codcel's `FORECAST.ETS.STAT` implementation compares to Microsoft Excel, including what matches exactly and where to expect differences.

## Summary

| Scenario | Match with Excel | Typical Difference |
|----------|------------------|--------------------|
| Step size (stat_type=8) | Exact | 0 |
| Smoothing parameters — seasonal with perfect-fit data | Exact | 0 |
| Error metrics — seasonal with perfect-fit data | Exact | 0 |
| Smoothing parameters — seasonal with general data | Approximate | Varies |
| Error metrics — seasonal with general data | Approximate | Varies |
| Smoothing parameters — non-seasonal (EDS mode) | Close | 0.002 – 0.25 |
| Error metrics — non-seasonal (EDS mode) | Close | 0.1 – 5 |

## What Matches Excel Exactly

### Step Size (stat_type=8)

The detected timeline step size matches Excel exactly for all tested configurations:

- Monthly data: **31.0** (regardless of seasonality, data_completion, or aggregation)
- Quarterly data: **90.0** (regardless of seasonality, data_completion, or aggregation)

This holds across all 28 step integration tests.

### Seasonal with Perfect-Fit Data (stat_type=1–7)

When the seasonal ETS model achieves a perfect fit on the training data (e.g. a repeating pattern like `[a, b, c, d, a+20, b+20, c+20, d+20, ...]` with period 4), both Codcel and Excel converge to the same smoothing parameters and produce zero error metrics. In this case, all stat types match exactly.

| Stat Type | Monthly (period=12) | Quarterly (period=4) |
|-----------|--------------------|--------------------|
| 1 — Alpha | 0.166667 | 0.751 |
| 2 — Beta | 0.083333 | 0.001 |
| 3 — Gamma | 0.75 | 0.001 |
| 4 — MASE | 0.0 | 0.0 |
| 5 — SMAPE | 0.0 | 0.0 |
| 6 — MAE | 0.0 | 0.0 |
| 7 — RMSE | 0.0 | 0.0 |

These results hold across all data_completion and aggregation variants (28+ tests).

**Note:** This exact match occurs because when the model fits perfectly, any reasonable optimizer will converge to the same global minimum. For general data where the fit is imperfect, Codcel's CMLE optimizer may find a different local minimum than Excel's proprietary algorithm — see "Seasonal with General Data" below.

### Supported Parameters

All six parameters of `FORECAST.ETS.STAT` are implemented:

| Parameter | Support |
|-----------|---------|
| `values` | Full support |
| `timeline` | Full support |
| `stat_type` | 1–8 (Alpha, Beta, Gamma, MASE, SMAPE, MAE, RMSE, Step) |
| `seasonality` | 0 (none), 1 (auto-detect), or explicit period |
| `data_completion` | 0 (fill zeros) or 1 (interpolate, default) |
| `aggregation` | 1 (average), 2–3 (count), 4 (max), 5 (median), 6 (min), 7 (sum) |

## Where Differences Occur

### Seasonal with General Data (stat_type=1–7)

For data that does not produce a perfect fit, Codcel's concentrated MLE optimizer may find different smoothing parameters than Excel's proprietary algorithm. The resulting parameter and error metric differences depend on the data and seasonal period.

Standard periods (4, 12) tend to produce smaller differences than non-standard periods (2, 3, 6). See the FORECAST.ETS documentation for specific diff values by period.

### Non-Seasonal Smoothing Parameters (stat_type=1–3)

When seasonality is disabled (`seasonality=0`) or auto-detection finds no seasonal pattern, the EDS (Exponential Double Smoothing) optimizer produces slightly different smoothing parameters than Excel.

**Monthly data (EDS mode):**

| Stat Type | Excel | Codcel | Difference |
|-----------|-------|--------|------------|
| 1 — Alpha | 0.998 | ~1.0 | +0.002 |
| 2 — Beta | 0.001 | ~0.0 | −0.001 |
| 3 — Gamma | ~0.0 | 0.0 | ~0 |

**Quarterly data (EDS mode, seasonality=0):**

| Stat Type | Excel | Codcel | Difference |
|-----------|-------|--------|------------|
| 1 — Alpha | 0.25 | ~0.0 | −0.25 |
| 2 — Beta | 0.001 | ~0.0 | −0.001 |
| 3 — Gamma | 0.001 | 0.0 | −0.001 |

The quarterly EDS case shows a larger Alpha difference. This is because Codcel's Nelder-Mead optimizer with concentrated MLE finds a different local minimum (near-zero smoothing, equivalent to OLS linear regression) compared to Excel's proprietary algorithm. Both produce valid forecasts — the point forecast difference is only ~0.12 for this data.

### Non-Seasonal Error Metrics (stat_type=4–7)

Error metrics depend on the fitted model's one-step-ahead residuals, so they inherit any smoothing parameter differences from the optimizer.

**Monthly data (EDS mode):**

| Stat Type | Excel | Codcel (expected) | Notes |
|-----------|-------|-------------------|-------|
| 4 — MASE | 0.678 | Close | Depends on alpha/beta fit |
| 5 — SMAPE | 0.013 | Close | Depends on alpha/beta fit |
| 6 — MAE | 3.730 | Close | Depends on alpha/beta fit |
| 7 — RMSE | 4.581 | Close | Depends on alpha/beta fit |

**Quarterly data (EDS mode, seasonality=0):**

| Stat Type | Excel | Codcel (expected) | Notes |
|-----------|-------|-------------------|-------|
| 4 — MASE | 0.577 | Approximate | Larger difference due to alpha divergence |
| 5 — SMAPE | 0.051 | Approximate | Larger difference due to alpha divergence |
| 6 — MAE | 8.659 | Approximate | Larger difference due to alpha divergence |
| 7 — RMSE | 12.027 | Approximate | Larger difference due to alpha divergence |

## Why Differences Occur

### Excel's Proprietary Optimizer

The differences in smoothing parameters trace to the same root cause documented in the [FORECAST.ETS](forecast__ets.md) and [FORECAST.ETS.CONFINT](forecast__ets__confint.md) pages:

- Excel uses an undocumented, proprietary optimization algorithm for ETS
- No open-source implementation (including Python's `statsmodels`) has replicated Excel's exact parameters
- Codcel uses Nelder-Mead optimization with concentrated Maximum Likelihood Estimation for both seasonal and non-seasonal modes
- Our optimizer finds the mathematically optimal (minimum SSE) solution, which sometimes differs from Excel's

The smoothing parameters reported by `FORECAST.ETS.STAT` are the same parameters used internally by `FORECAST.ETS` and `FORECAST.ETS.CONFINT`. The consistency of differences across all three functions confirms a single root cause in the optimizer.

### Why Error Metrics Differ

Error metrics (MASE, SMAPE, MAE, RMSE) are computed from one-step-ahead forecast residuals:

```
residual[i] = forecast[i] - actual[i]    for i = 1, ..., n-1
```

where `forecast[i]` is the model's one-step-ahead prediction using parameters fitted up to point `i-1`. Since the smoothing parameters differ, the one-step-ahead forecasts differ, and thus the residuals and error metrics differ.

When the seasonal ETS model achieves a perfect fit (error metrics = 0), both Codcel and Excel agree exactly — there are no residuals to disagree about.

### Why Step Size Always Matches

The step size (stat_type=8) is a property of the input timeline, not the fitted model. It is computed before any optimization occurs:

- For quarterly dates (all on 1st of month): minimum gap between consecutive dates = 90 days
- For monthly dates (all on 1st of month): first gap = 31 days (January)

The step calculation does not depend on the optimizer, so there are no proprietary algorithm differences.

## Technical Details

### Stat Type Mapping

| stat_type | Name | What It Returns |
|-----------|------|-----------------|
| 1 | Alpha | Level smoothing parameter (model.alpha) |
| 2 | Beta | Trend smoothing parameter (model.gamma in LO convention) |
| 3 | Gamma | Seasonal smoothing parameter (model.beta in LO convention); 0.0 for non-seasonal |
| 4 | MASE | Mean Absolute Scaled Error: MAE / mean(\|Y[i] - Y[i-1]\|) |
| 5 | SMAPE | Symmetric Mean Absolute Percentage Error |
| 6 | MAE | Mean Absolute Error of one-step-ahead forecasts |
| 7 | RMSE | Root Mean Square Error of one-step-ahead forecasts |
| 8 | Step | Detected timeline step size in original date serial units |

### Parameter Naming Convention

Codcel swaps beta and gamma relative to standard textbooks:

| Excel Output | Codcel Internal | Hyndman Textbook | Role |
|-------------|--------------------------|-----------------|------|
| Alpha (stat_type=1) | `model.alpha` | α | Level smoothing |
| Beta (stat_type=2) | `model.gamma` | β | Trend smoothing |
| Gamma (stat_type=3) | `model.beta` | γ | Seasonal smoothing |

### Step Size Computation

The step size uses a hybrid approach to handle calendar irregularities:

1. Sort and aggregate the timeline (same preprocessing as FORECAST.ETS)
2. If month-day detection fires (all dates share the same day-of-month):
   - Compute step in month-number space
   - If step = 1 month: return the first difference in the original timeline (avoids February's 28-day distortion)
   - If step > 1 month: return `compute_min_step` on the original timeline
3. If no month-day detection: return `compute_min_step` on the original timeline

### Algorithm Selection

| Condition | Optimizer | Matches Excel |
|-----------|-----------|--------------|
| Seasonal, perfect-fit data | Nelder-Mead with concentrated MLE | Exact |
| Seasonal, general data, standard period (4, 12) | Nelder-Mead with concentrated MLE | Close |
| Seasonal, general data, non-standard period | Nelder-Mead with concentrated MLE | Approximate |
| Non-seasonal (EDS) | Nelder-Mead with concentrated MLE | Close |

### Error Metric Formulas

All error metrics exclude index 0 (since `forecast[0] = values[0]` always):

```
MAE   = (1/(n-1)) × Σ |forecast[i] - values[i]|          for i = 1..n-1
RMSE  = √((1/(n-1)) × Σ (forecast[i] - values[i])²)      for i = 1..n-1
SMAPE = (1/(n-1)) × Σ |F[i]-Y[i]| / ((|Y[i]|+|F[i]|)/2) for i = 1..n-1
MASE  = MAE / mean(|Y[i] - Y[i-1]|)                       for i = 1..n-1
```

## Validation Summary

- All generated integration tests pass
- Step tests (28 tests) match Excel exactly
- Seasonal tests with perfect-fit data match Excel exactly
- Seasonal tests with general data are close to Excel; differences reflect different optimizer local minima
- Non-seasonal tests show the same proprietary algorithm differences as FORECAST.ETS and FORECAST.ETS.CONFINT



### Applications:

- **Model Validation:** Use MASE and SMAPE to evaluate whether the ETS model fits your data well before relying on
  `FORECAST.ETS` predictions.
- **Parameter Tuning:** Inspect smoothing parameters to understand how the model weighs recent vs. older data.
- **Model Comparison:** Compare error metrics across different seasonality settings to determine the best model
  configuration for your data.
- **Reporting:** Include RMSE or MAE in forecast reports to communicate prediction uncertainty to stakeholders.
- **Data Quality Checks:** Use the step size (stat_type 8) to verify that your timeline data is interpreted correctly.

> **Tip:** Use `FORECAST.ETS.STAT` with `stat_type=4` (MASE) to quickly assess whether exponential smoothing is
> appropriate for your data. If MASE is greater than 1, the ETS model performs worse than a naive forecast, and you
> may want to consider alternative approaches such as `FORECAST.LINEAR`.