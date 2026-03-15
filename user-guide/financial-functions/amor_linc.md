<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# AMORLINC Function

The `AMORLINC` function in Excel is used to calculate the **depreciation for each accounting period** using the
**straight-line depreciation method**. This function is typically used for financial depreciation calculations where
assets lose value at a consistent rate over their useful life.

## Key Features of `AMORLINC`:

- Calculates depreciation using the linear (straight-line) method.
- Prorates depreciation for partial periods based on the date of acquisition.
- Commonly applied in financial and fixed asset management for tracking uniform depreciation expenses.

## Syntax:

```plaintext
AMORLINC(cost, date_purchased, first_period, salvage, period, rate, [basis])
```

- **cost**: The cost of the asset being depreciated.
- **date_purchased**: The date when the asset was purchased.
- **first_period**: The end date of the first depreciation period.
- **salvage**: The expected residual value (salvage value) of the asset after its useful life.
- **period**: The specific period for which you want to calculate the depreciation.
- **rate**: The depreciation rate (as a percentage).
- **[basis]**: (Optional) Specifies which day count base to use. Defaults to `0`. The options are:
    - `0` = US (NASD) 30/360 (default).
    - `1` = Actual/actual.
    - `3` = Actual/365.
    - `4` = European 30/360.

## How `AMORLINC` Works:

1. Distributes the asset's cost minus its salvage value evenly over its useful life.
2. Considers the acquisition date when prorating depreciation for the first and last periods.
3. Calculates depreciation progressively for selected periods, allowing for uniform expense allocation.

## Examples:

### 1. Calculating Depreciation for the First Year:

```excel
=AMORLINC(10000, DATE(2023,1,1), DATE(2023,12,31), 500, 1, 0.1)
```

**Result:** Returns the depreciation for the first period of an asset priced at 10,000 with a 10% depreciation rate and
a residual value of 500.

### 2. Depreciation for the Third Period Using a Custom Basis:

```excel
=AMORLINC(8000, DATE(2022,7,1), DATE(2022,12,31), 1000, 3, 0.2, 1)
```

**Result:** Calculates depreciation for the third period with a 20% depreciation rate, considering the **Actual/actual**
day count method.

### 3. Straight-Line Depreciation with Higher Salvage Value:

```excel
=AMORLINC(12000, DATE(2023,4,1), DATE(2024,3,31), 2000, 2, 0.15)
```

**Result:** Returns the depreciation for the second period based on a 15% depreciation rate for an asset costing 12,000
with a salvage value of 2,000.

## Notes:

- If the **cost**, **date_purchased**, **salvage**, or **rate** values are invalid, Excel will return a `#VALUE!` error.
- Ensure that the **salvage** value is less than the asset's cost, as depreciation cannot proceed if the salvage value
  is equal to or greater than the initial cost.
- The **basis** parameter affects how periods are calculated and can have a slight influence on depreciation timing.

## Applications:

- **Property and Fixed Asset Management**: Accurately track asset depreciation under straight-line rules.
- **Tax Accounting**: Use for financial statements where linear depreciation is required.
- **Corporate Financial Reporting**: Assign consistent depreciation amounts over the useful life of fixed assets.

> **Tip:** Always verify inputs like dates and rates to align with your organization's financial policies or local
accounting regulations.