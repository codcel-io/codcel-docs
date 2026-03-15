<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DDB Function

The `DDB` function in Excel calculates the **depreciation of an asset** for a specified period using the *
*double-declining balance method**. This method accelerates depreciation, allocating larger amounts in the earlier years
of an asset's life and smaller amounts in later years.

## Key Features of DDB:

- Returns the depreciation expense for a specified period.
- Uses the double-declining balance method, which applies a higher depreciation rate in the beginning to reflect the
  faster usage or aging of the asset in its early years.
- Automatically switches to the straight-line depreciation method when it results in higher depreciation than the
  declining balance method for the remaining useful life.

## Syntax:

```plaintext
DDB(cost, salvage, life, period)
```

- **cost**: The initial cost of the asset before depreciation.
- **salvage**: The value of the asset at the end of its useful life (residual value).
- **life**: The total number of periods (usually years) over which the asset is depreciated.
- **period**: The period for which you want to calculate the depreciation amount (must be between 1 and the asset's
  life).
- `factor` (optional) specifies the rate of depreciation acceleration (defaults to 2 for double-declining balance).

## How It Works:

1. The function calculates the depreciation for a specified period by applying the **double-declining balance formula**:
   $$ \text{Depreciation} = \text{Book Value at Beginning of Period} \times \frac{2}{\text{Asset Life}} $$
2. The formula ensures the **salvage value** is not exceeded, meaning the depreciation will never reduce the asset's
   value below the salvage amount.
3. In later periods, when the calculated depreciation under the double-declining balance method would result in
   depreciation lower than the straight-line method, the function automatically switches to the straight-line method.

## Examples:

### 1. Depreciation in the 1st Year of an Asset:

```excel
=DDB(10000, 1000, 5, 1)
```

**Result:** Calculates the depreciation in the first year for an asset with an initial cost
of $10,000, a salvage value of $1,000, and a 5-year useful life.

### 2. Depreciation in the 3rd Year:

```excel
=DDB(20000, 4000, 8, 3)
```

**Result:** Computes the depreciation for the 3rd year for an asset costing $20,000, with a salvage value of $4,000 and
a useful life of 8 years.

### 3. Depreciation for a Shorter Useful Life:

```excel
=DDB(15000, 500, 4, 2)
```

**Result:** Returns the depreciation for the 2nd year of a $15,000 asset, salvaged at $500, and depreciated over 4
years.

## Notes:

- The **life** and **period** must use the same units (e.g., both in years or both in months).
- When the depreciation for the remaining periods under double-declining balance becomes less than the straight-line
  depreciation, the function switches to the straight-line method to ensure accurate salvage value.
- If the provided input arguments are invalid, Excel may return errors such as:
    - `#NUM!` (e.g., if `period` is less than 1 or greater than `life`).
    - `#VALUE!` (e.g., non-numeric inputs are given).

## Applications:

- **Accelerated Depreciation**: Ideal for scenarios where assets depreciate faster at the start of their useful life,
  such as vehicles, computers, or machinery.
- **Tax Calculations**: Helps calculate higher depreciation deductions in the early years, which may reduce taxable
  income.
- **Asset Valuation**: Useful for estimating the declining value of assets over time in financial analysis or
  accounting.

> **Tip:** Use the `DDB` function to calculate depreciation expenses when you expect the asset to lose value at a faster
> rate initially. For a more uniform depreciation rate, consider using `SLN` (straight-line method) instead.