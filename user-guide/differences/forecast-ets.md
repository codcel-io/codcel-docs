<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# FORECAST.ETS Precision

The `FORECAST.ETS` function implements Exponential Triple Smoothing for time-series forecasting. Codcel's implementation closely matches Excel for most cases, but there are known precision differences in specific scenarios.

---

## Seasonal Forecasting (ETS)

For standard seasonal forecasting with auto-detected periods (e.g., quarterly data with period 4), Codcel matches Excel's results exactly.

---

## Non-Seasonal Forecasting (EDS)

For non-seasonal forecasting (Exponential Double Smoothing), Excel uses a proprietary algorithm that no known open-source implementation has replicated exactly.

Codcel uses an ETS(A,A,N) innovations model with concentrated Maximum Likelihood Estimation, which produces results equivalent to Ordinary Least Squares regression. This approach gives very close but not identical results to Excel.

### Example

For a 12-point quarterly dataset:

| Implementation | Result |
|---------------|--------|
| Excel | 191.25 |
| Codcel | 191.36 |
| Python statsmodels | 191.36 |

The difference is approximately **0.12** for this dataset. Both Codcel and Python's statsmodels produce the same result, suggesting that Excel's internal algorithm is the outlier.

---

## Recommendations

- For seasonal forecasts, Codcel and Excel match closely
- For non-seasonal forecasts, expect small differences (typically less than 0.2)
- If exact Excel parity is critical for your use case, consider validating FORECAST.ETS results against your specific dataset using the generated test documentation