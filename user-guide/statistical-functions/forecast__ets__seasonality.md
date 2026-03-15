<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## FORECAST.ETS.SEASONALITY Function

The `FORECAST.ETS.SEASONALITY` function in Excel returns the length of the **seasonal pattern** that the
**Exponential Smoothing (ETS)** algorithm detects in the specified time series data. This function is useful for
understanding the repeating cycle length in your data before running `FORECAST.ETS` or `FORECAST.ETS.CONFINT`.

### Key Features of FORECAST.ETS.SEASONALITY:

- Returns a single integer representing the detected seasonal period length.
- Uses the same **exponential triple smoothing** detection algorithm as `FORECAST.ETS`.
- Helps you understand and validate the seasonal structure of your data before forecasting.
- Supports the same data completion and aggregation options as `FORECAST.ETS`.

### Syntax:

```plaintext
FORECAST.ETS.SEASONALITY(values, timeline, [data_completion], [aggregation])
```

#### Arguments:

1. **values** *(required)*:
   The dependent data set (historical data) containing the values to be analyzed for seasonal patterns.

2. **timeline** *(required)*:
   The independent set of dates or time periods corresponding to the `values`.
   *The timeline must have consistent steps (e.g., daily, monthly intervals) and cannot contain duplicates.*

3. **data_completion** *(optional)*:
   Specifies how to handle missing data points:
    - `0`: Missing data treated as zero.
    - `1`: (Default) Missing data completed using the average of neighboring points.

4. **aggregation** *(optional)*:
   Controls how duplicate timestamps in the timeline are aggregated. Default is `AVERAGE`.
   Options include `SUM`, `COUNT`, `MEDIAN`, etc.

---

### How It Works:

The `FORECAST.ETS.SEASONALITY` function analyzes the historical data to detect repeating patterns. It uses the same
seasonal detection algorithm that `FORECAST.ETS` uses internally when `seasonality` is set to `1` (auto-detect).

The function returns:
- A **positive integer** representing the number of data points in one full seasonal cycle (e.g., `4` for quarterly
  seasonality, `12` for monthly data with yearly seasonality).
- **`1`** if no seasonal pattern is detected in the data.

This is equivalent to calling `FORECAST.ETS` with `seasonality=1` and inspecting which seasonal period it selects
internally.

---

### Examples:

1. **Detecting Seasonality in Monthly Sales Data:**

   Assume the following:
    - Sales data is in `B2:B25` (24 months of monthly sales).
    - Corresponding months are in `A2:A25`.

   Use the formula:

   ```excel
   =FORECAST.ETS.SEASONALITY(B2:B25, A2:A25)
   ```

   If the sales data has a yearly repeating pattern, this returns `12`.

2. **Checking Quarterly Data for Seasonal Patterns:**

   With quarterly data in `B2:B13` and dates in `A2:A13`:

   ```excel
   =FORECAST.ETS.SEASONALITY(B2:B13, A2:A13)
   ```

   If the data follows an annual cycle, this returns `4`. If no pattern is detected, it returns `1`.

3. **Handling Missing Data:**

   If you want missing values in `B2:B25` to be treated as `0` during detection:

   ```excel
   =FORECAST.ETS.SEASONALITY(B2:B25, A2:A25, 0)
   ```

4. **With Aggregated Duplicates:**

   In scenarios where the timeline has duplicate entries (e.g., data from multiple sources for the same date):

   ```excel
   =FORECAST.ETS.SEASONALITY(C2:C50, D2:D50, 1, "SUM")
   ```

   This sums up duplicate values in `D2:D50` before analyzing for seasonality.

5. **Using the Result with FORECAST.ETS:**

   You can use `FORECAST.ETS.SEASONALITY` to explicitly pass the detected period to `FORECAST.ETS`:

   ```excel
   =FORECAST.ETS(A26, B2:B25, A2:A25, FORECAST.ETS.SEASONALITY(B2:B25, A2:A25))
   ```

   This is functionally equivalent to using `seasonality=1` (auto-detect), but makes the seasonal period explicit and
   visible in your spreadsheet.

---

# FORECAST.ETS.SEASONALITY — Excel Compatibility Notes

This document describes how Codcel's `FORECAST.ETS.SEASONALITY` implementation compares to Microsoft Excel, including what matches exactly and where to expect differences.

## Summary

| Scenario | Match with Excel | Notes |
|----------|------------------|-------|
| Data with clear seasonal pattern | Exact | Returns same period length |
| Data without seasonal pattern | Exact | Returns 1 |
| Monthly data with yearly cycle | Exact | Returns 12 |
| Quarterly data with yearly cycle | Exact | Returns 4 |
| Insufficient data for detection | Exact | Returns 1 |

## What Matches Excel Exactly

### Seasonal Period Detection

`FORECAST.ETS.SEASONALITY` uses the same seasonal detection algorithm as `FORECAST.ETS` with `seasonality=1`. Since Codcel's `FORECAST.ETS` matches Excel exactly for seasonal forecasting, the seasonal period detection also matches.

The function correctly identifies standard seasonal periods:
- **12** for monthly data with yearly seasonality
- **4** for quarterly data with yearly seasonality
- **7** for daily data with weekly seasonality
- **1** when no seasonal pattern exists

### Supported Parameters

All four parameters of `FORECAST.ETS.SEASONALITY` are implemented:

| Parameter | Support |
|-----------|---------|
| `values` | Full support |
| `timeline` | Full support |
| `data_completion` | 0 (fill zeros) or 1 (interpolate, default) |
| `aggregation` | 1 (average), 2–3 (count), 4 (max), 5 (median), 6 (min), 7 (sum) |

### Data Completion and Aggregation

Tests with `data_completion=0`, `data_completion=1`, and various aggregation modes all produce the same results as Excel.

## Where Differences May Occur

### Edge Cases with Ambiguous Seasonality

When data contains multiple possible seasonal periods of similar strength (e.g., both semi-annual and annual patterns), the detected period may occasionally differ from Excel. These cases are rare and typically involve synthetic or unusual data sets.

### Minimum Data Requirements

Both Excel and Codcel require a minimum number of data points to detect seasonality. At least two full seasonal cycles are generally needed (e.g., 24 months for yearly seasonality detection). With fewer data points, both implementations return `1` (no seasonality detected).

## Technical Details

### Algorithm

The seasonal detection algorithm works by:

1. **Detrending** the data to remove the linear trend component.
2. **Computing autocorrelation** at each candidate lag from 2 to N/2 (where N is the number of data points).
3. **Selecting the lag** with the highest autocorrelation that exceeds a significance threshold.
4. **Returning 1** if no lag exceeds the threshold, indicating no seasonality.

This is the same algorithm used internally by `FORECAST.ETS` when `seasonality=1`.

### Error Conditions

The following match Excel's behaviour:
- Mismatched array lengths → returns `#N/A` error
- Insufficient data points → returns `#VALUE!` error
- Non-numeric values → returns `#VALUE!` error

### Applications:

- **Data Exploration:** Quickly determine whether your time series data contains seasonal patterns before building
  forecasts.
- **Forecast Validation:** Verify the seasonal period used by `FORECAST.ETS` by checking it explicitly.
- **Dynamic Reporting:** Use the result in formulas to automatically adapt forecasts and charts based on detected
  seasonality.
- **Model Selection:** Decide whether to use `FORECAST.ETS` (seasonal) or `FORECAST.LINEAR` (non-seasonal) based on
  whether seasonality is detected.

> **Tip:** Use `FORECAST.ETS.SEASONALITY` to check your data before running `FORECAST.ETS`. If the function returns `1`
> (no seasonality), consider using `FORECAST.LINEAR` for simpler and potentially more accurate non-seasonal forecasting.
> You can also use this function to validate that `FORECAST.ETS` is detecting the seasonal period you expect.