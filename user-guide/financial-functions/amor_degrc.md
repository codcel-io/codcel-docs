<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# AMORDEGRC Function

The `AMORDEGRC` function in Excel is used to calculate the **depreciation of an asset** for each accounting period using
the **French accounting system**, with a depreciation coefficient that increases the rate of decay based on the asset's
life span. This function is particularly useful for financial and tax accounting purposes, especially when an
accelerated depreciation method is required.

## Key Features of AMORDEGRC:

- Calculates depreciation using a declining balance method with a specific coefficient.
- Applies to financial accounting systems, particularly those following French norms for depreciation.
- Adjusts the depreciation for changes in asset life span or prorates based on the date of acquisition.

## Syntax:

```plaintext
AMORDEGRC(cost, date_purchased, first_period, salvage, period, rate, [basis])
```

- **cost**: The cost of the asset being depreciated.
- **date_purchased**: The date the asset was purchased.
- **first_period**: The end date of the first depreciation period.
- **salvage**: The salvage value (residual value) of the asset.
- **period**: The period for which you want to calculate depreciation.
- **rate**: The depreciation rate (percentage).
- **[basis]**: (Optional) The day count basis to be used. Defaults to `0`. The options are:
    - `0` = US (NASD) 30/360 (default).
    - `1` = Actual/actual.
    - `3` = Actual/365.
    - `4` = European 30/360.

## Depreciation Coefficients:

The `AMORDEGRC` function uses specific coefficients based on the asset's life span:

- **Life Span ≤ 3 years** → Coefficient = 1.5
- **Life Span = 4–6 years** → Coefficient = 2.0
- **Life Span ≥ 7 years** → Coefficient = 2.5

## How It Works:

1. Calculates the depreciation expense for the given period using the declining balance method.
2. Adjusts the depreciation rate with the coefficient based on the asset’s life span.
3. Allocates prorated depreciation for the initial and final periods based on the purchase date and the end date of the
   first period.

## Examples:

### 1. Depreciation for an Asset with a 5-year Life Span:

```excel
=AMORDEGRC(10000, DATE(2023,1,1), DATE(2023,12,31), 500, 1, 0.2)
```

**Result:** Returns the depreciation amount for the first year with a coefficient of 2.0 (as the life span falls in the
4–6 years range).

### 2. Depreciation for an Asset with a 10-year Life Span:

```excel
=AMORDEGRC(5000, DATE(2022,7,1), DATE(2022,12,31), 300, 2, 0.1)
```

**Result:** Calculates the depreciation for the second period with a coefficient of 2.5 (life span ≥ 7 years).

### 3. Depreciation Using Different Day Count Basis:

```excel
=AMORDEGRC(7000, DATE(2024,4,1), DATE(2025,3,31), 100, 3, 0.15, 1)
```

**Result:** Returns depreciation using the Actual/actual method for the third period.

## Notes:

- If **date_purchased**, **first_period**, or **period** is invalid, Excel will return a `#VALUE!` error.
- Ensure the **rate** and **life span** are appropriate according to asset classification.
- The **salvage** value must be less than the initial cost, otherwise depreciation cannot proceed.
- Day count conventions (**basis**) affect how the depreciation is prorated within a period.

## Applications:

- **Financial Accounting**: Ensures compliance with French accelerated depreciation norms.
- **Tax Reporting**: Accurately calculates allowable depreciation deductions for tax returns.
- **Asset Management**: Facilitates tracking of depreciation for capital assets.

> **Tip:** Always ensure date inputs are valid Excel date values (e.g., `DATE(year, month, day)`) and that depreciation
rate and periods are consistent with the asset's usage and accounting rules.