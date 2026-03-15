<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SLN Function

The `SLN` function in Excel calculates the **straight-line depreciation** of an asset for a single period. It determines
the fixed amount by which the value of an asset decreases each period over its useful life.

### Key Features of SLN:

- Computes depreciation using the **straight-line method**.
- Useful for assets that lose value evenly over time.
- Can be used to plan and monitor the depreciation of fixed assets.

### Syntax:

```plaintext
SLN(cost, salvage, life)
```

- **cost**: The initial cost or purchase price of the asset.
- **salvage**: The residual value of the asset at the end of its useful life (the amount it will be worth after
  depreciation is complete).
- **life**: The total number of periods (e.g., years) over which the asset will be depreciated.

### Examples:

1. **Basic Depreciation Calculation**:
   `=SLN(10000, 2000, 5)`  
   Depreciates an asset purchased for $10,000 with a $2,000 salvage value over 5 years.  
   **Result**: `$1,600` per year.

2. **Shorter Useful Life**:
   `=SLN(5000, 0, 3)`  
   Depreciates an asset worth $5,000 with no salvage value over 3 years.  
   **Result**: `$1,666.67` per year.

3. **Higher Salvage Value**:
   `=SLN(20000, 8000, 4)`  
   Depreciates an asset costing $20,000 with an $8,000 salvage value over 4 years.  
   **Result**: `$3,000` per year.

### Notes:

- The **straight-line method** assumes the asset depreciates by the same amount in each period, making it simple and
  easy to use.
- The **salvage value** must be less than the **cost**, and both should be positive numbers.
- The **life** value is entered as the number of periods (typically years).
- If the **salvage value** is `0`, the asset is fully depreciated over its lifespan.
- Returns a fixed numeric value representing the depreciation amount for one period.

> **Tips**:
> - Use `SLN` for calculating fixed depreciation values when preparing balance sheets or financial reports.
> - Pair this with other Excel financial tools (e.g., `DB` or `DDB`) for more complex depreciation analyses.
> - Ensure the **life** matches the expected measurement period (e.g., years vs. months) to avoid miscalculation.