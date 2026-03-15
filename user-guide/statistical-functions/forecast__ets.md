<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FORECAST.ETS Function

The `FORECAST.ETS` function in Excel is used to predict a future value using the **Exponential Smoothing (ETS)**
algorithm. This function is particularly powerful for **time series forecasting**, making it suitable for data that
displays seasonal patterns.

### Key Features of FORECAST.ETS:

- Produces forecasts based on **exponentially weighted time series smoothing**.
- Automatically detects **seasonal patterns** within the data.
- Can be used for short-term and long-term forecasting.
- Suitable for businesses and data analysts working with periodic or recurring trends.

### Syntax:

```plaintext
FORECAST.ETS(target_date, values, timeline, [seasonality], [data_completion], [aggregation])
```

#### Arguments:

1. **target_date** *(required)*:  
   The date (or time) for which you want to forecast a future value.  
   *Must be a numeric value or valid date/time format.*

2. **values** *(required)*:  
   The dependent data set (historical data) containing the values to be forecasted.

3. **timeline** *(required)*:  
   The independent set of dates or time periods corresponding to the `values`.  
   *The timeline must have consistent steps (e.g., daily, monthly intervals) and cannot contain duplicates.*

4. **seasonality** *(optional)*:  
   A numeric value to specify the length of the seasonal pattern. Options:
    - `0`: No seasonality (produces a non-seasonal forecast).
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

The `FORECAST.ETS` function is based on the **exponential triple smoothing** model, which applies smoothing to:

- The data’s level (current average).
- Trend (growth or decline over time).
- Seasonality (patterns that repeat at regular intervals).

This method adapts based on the weights assigned to recent versus older data points, producing more accurate
predictions, particularly for recurring patterns.

---

### Examples:

1. **Predicting Monthly Sales Data:**

   Assume the following:
    - Sales data is in `B2:B13` (monthly sales).
    - Corresponding months are in `A2:A13`.
    - You want to forecast sales for the month in cell `A14`.

   Use the formula:

   ```excel
   =FORECAST.ETS(A14, B2:B13, A2:A13, 12)
   ```

   This predicts the sales for the `A14` month considering a yearly (12-month) seasonality.

2. **Automatic Seasonality Detection:**

   Suppose your timeline (`A1:A36`) represents daily data over multiple months. If you want `FORECAST.ETS` to
   automatically detect the seasonality:

   ```excel
   =FORECAST.ETS(TODAY()+7, B1:B36, A1:A36)
   ```

   This forecasts the value 7 days from the current date based on the daily historical data.

3. **Handling Missing Data:**

   If you want to treat missing values in `B2:B13` as `0`:

   ```excel
   =FORECAST.ETS(A14, B2:B13, A2:A13, 1, 0)
   ```

4. **Forecast with Aggregated Duplicates:**

   In scenarios where the timeline has duplicate entries (e.g., sales data for the same date from multiple stores), use
   aggregation:

   ```excel
   =FORECAST.ETS(A14, C2:C50, D2:D50, 1, 1, "SUM")
   ```

   This sums up duplicate values in `D2:D50` before forecasting.

---

### Notes:

# FORECAST.ETS — Excel Compatibility Notes

This document describes how Codcel's `FORECAST.ETS` implementation compares to Microsoft Excel, including what matches exactly and where to expect differences.

## Summary

| Scenario | Match with Excel | Typical Difference |
|----------|------------------|--------------------|
| Seasonal forecasting, standard period (4 or 12) | Close | 0 – 0.5 |
| Seasonal forecasting, non-standard period (2, 3, 6) | Approximate | 1 – 12 |
| Within-range target dates | Exact | 0 |
| Non-seasonal forecasting (seasonality = 0) | Close | 0.1 – 5 |
| Monthly data with auto-detected seasonality and no seasonal pattern | Close | 1 – 5 |

## What Matches Excel Exactly

### Within-Range Targets

When the target date falls within the data range, `FORECAST.ETS` returns the actual observed value (with linear interpolation between points if needed). This matches Excel's behaviour exactly.

### Supported Parameters

All six parameters of `FORECAST.ETS` are implemented:

| Parameter | Support |
|-----------|---------|
| `target_date` | Full support |
| `values` | Full support |
| `timeline` | Full support |
| `seasonality` | 0 (none), 1 (auto-detect), or explicit period |
| `data_completion` | 0 (fill zeros) or 1 (interpolate, default) |
| `aggregation` | 1 (average), 2–3 (count), 4 (max), 5 (median), 6 (min), 7 (sum) |

### Date Handling

- Monthly timelines are automatically detected and converted to uniform month-number spacing
- The Lotus 1-2-3 1900 date bug (Excel serial date 60 = Feb 29, 1900) is handled correctly for Excel compatibility
- Quarterly and other regular intervals work with raw serial date spacing

## Where Differences Occur

### Seasonal Forecasting (ETS)

Codcel uses concentrated MLE with Nelder-Mead optimization for the seasonal ETS model. This produces results that are close to but not identical to Excel's proprietary algorithm.

**Example:** 12 observations with values=[100,120,135,160,110,130,145,170,115,140,155,180], timeline=[1..12], target=13:

| Seasonality Period | Excel | Codcel | Difference |
|--------------------|-------|--------|------------|
| 4 (standard quarterly) | 127.58 | 128.08 | 0.50 |
| 2 | 151.95 | 153.16 | 1.22 |
| 3 | 175.71 | 182.67 | 6.96 |
| 6 | 172.29 | 184.58 | 12.29 |

Standard periods (4 and 12) produce the smallest differences. Non-standard periods (2, 3, 6) can produce larger differences where the optimization landscape has multiple local minima.

When the seasonal model achieves a perfect fit on the training data (e.g. a repeating pattern [a, b, c, d, a+20, b+20, ...] with period 4), both algorithms converge to the same result and the match is exact.

### Non-Seasonal Forecasting (EDS Mode)

When `seasonality=0` (explicitly disabled), the function uses Exponential Double Smoothing (EDS) instead of the full ETS model. In this mode, Codcel's results differ slightly from Excel.

**Example:** 12 quarterly observations with `seasonality=0`, forecasting one period ahead:
- Excel: **191.25**
- Codcel: **191.36**
- Difference: **0.12** (0.06%)

**Why this happens:** Excel uses a proprietary optimization algorithm for non-seasonal ETS that jointly optimizes smoothing parameters and initial states. The exact algorithm has not been publicly documented and no open-source implementation (including Python's `statsmodels` library) has been able to replicate Excel's result exactly. Codcel uses a concentrated Maximum Likelihood Estimation (MLE) approach with the ETS(A,A,N) innovations state-space model, which produces the mathematically optimal (minimum SSE) solution.

Interestingly, our result has a _lower_ sum of squared errors than Excel's, suggesting Excel applies some form of undocumented regularization or constraint.

### Monthly Data Without Seasonal Pattern

When monthly data is provided but no clear seasonal pattern exists (either `seasonality=0` or auto-detection finds none), the same EDS algorithm difference applies. Expected differences are typically 1–5 units depending on the data scale and forecast horizon.

| Test Case | Excel | Codcel | Difference |
|-----------|-------|--------|------------|
| Basic monthly, 1 step ahead | 278.11 | 277.0 | 1.1 |
| Monthly, 2 steps ahead | 281.23 | 283.0 | 1.8 |
| Monthly, far future | 315.49 | 313.0 | 2.5 |

## Why Differences Occur

### Excel's Proprietary Algorithm

Excel's `FORECAST.ETS` uses an undocumented, proprietary optimization algorithm. This has been confirmed by multiple independent sources:

- **Python's `statsmodels`** produces results matching Codcel (not Excel) for the same data
- **LibreOffice Calc** uses a different approach (nested bisection) that matches Excel for some cases but not others
- No open-source implementation has replicated Excel's exact results across all configurations

Analysis of Excel's results shows that Excel does **not** minimize the sum of squared errors (SSE). For the standard test data with m=4, Excel's SSE is 16.88 compared to the optimal SSE of 11.25. This suggests Excel applies undocumented constraints or regularization during optimization.

### Codcel's Approach

Codcel uses **Nelder-Mead optimization with concentrated Maximum Likelihood Estimation** for both seasonal and non-seasonal modes:

- **Seasonal (ETS AAA):** For each candidate set of smoothing parameters (α, β, γ), the initial states (level, trend, and m seasonal components) are computed analytically via least-squares regression (concentrated MLE). Only the 3 smoothing parameters are optimized by Nelder-Mead. Multiple starting points are tried to reduce sensitivity to local minima. Parameters are constrained to [0, 0.99].

- **Non-seasonal (EDS AAN):** For each candidate pair (α, γ), the initial level and trend are computed analytically. The 2 smoothing parameters are optimized by Nelder-Mead with concentrated MLE.

Both paths find mathematically optimal (minimum SSE) solutions, which sometimes differ from Excel's proprietary optimizer.

## Technical Details

### Model Form

The ETS(A,A,A) innovations state-space model (seasonal):

```
e[t] = Y[t] - (l[t] + b[t] + s[t])
l[t+1] = l[t] + b[t] + alpha * e[t]
b[t+1] = b[t] + gamma * e[t]
s[t+m] = s[t] + beta * e[t]
```

The ETS(A,A,N) innovations state-space model (non-seasonal):

```
e[t] = Y[t] - (l[t] + b[t])
l[t+1] = l[t] + b[t] + alpha * e[t]
b[t+1] = b[t] + gamma * e[t]
```

### Parameter Naming Convention


| Codcel | Hyndman Textbook | Role |
|--------|-----------------|------|
| `alpha` | α | Level smoothing |
| `gamma` | β | Trend smoothing |
| `beta` | γ | Seasonal smoothing |

### Validation

- Python's `statsmodels.tsa.holtwinters.ExponentialSmoothing` produces the same result as Codcel for non-seasonal data (191.36 vs Excel's 191.25), confirming the difference is Excel-specific
- Seasonal test cases with standard periods are very close to Excel (diff < 1.0)
- All generated integration tests pass


### Applications:

- **Sales Projections:** Analyze seasonal trends in monthly or quarterly sales.
- **Energy Consumption Forecasting:** Predict electricity usage influenced by weather patterns or seasonal demand.
- **Inventory Management:** Estimate future stock requirements based on past trends.
- **Project Planning:** Forecast labor or resource utilization in cyclical project phases.

> **Tip:** If your data lacks clear seasonality, use the `FORECAST.ETS` function with `seasonality = 0`, or consider
> using the `FORECAST.LINEAR` function for simpler linear regression forecasting.