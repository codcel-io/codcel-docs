<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## SYD Function

The `SYD` function in Excel calculates the **sum-of-years' digits depreciation** of an asset for a specific period. This
method accelerates depreciation, allocating higher expenses during the earlier years of the asset's useful life and
lower expenses during later years.

### Key Features of SYD:

- Computes depreciation using the **sum-of-years' digits method**.
- Useful for assets that lose value more quickly at the beginning of their useful life.
- Provides a flexible way to account for rapid depreciation of certain types of assets.

### Syntax:

```plaintext
SYD(cost, salvage, life, period)
```

- **cost**: The initial cost or purchase price of the asset.
- **salvage**: The residual value of the asset at the end of its useful life (the amount it is expected to be worth
  after complete depreciation).
- **life**: The total number of periods (e.g., years) over which the asset will be depreciated.
- **period**: The specific period (e.g., year) for which you want to calculate the depreciation.

### Examples:

1. **Basic Depreciation Calculation**:
   `=SYD(10000, 2000, 5, 1)`  
   Depreciates an asset purchased for $10,000 with a $2,000 salvage value over 5 years, calculating depreciation for the
   1st year.  
   **Result**: `$2,666.67`

2. **Later Period Depreciation**:
   `=SYD(10000, 2000, 5, 4)`  
   Calculates depreciation in the 4th year for the same asset.  
   **Result**: `$533.33`

3. **Higher Salvage Value**:
   `=SYD(20000, 8000, 4, 2)`  
   Calculates depreciation in the 2nd year for an asset worth $20,000 with an $8,000 salvage value over 4 years.  
   **Result**: `$3,600`

### Notes:

- The **sum-of-years' digits method** applies a higher depreciation rate in the earlier years by dividing the remaining
  asset life by the sum of the digits of the asset life.
- The formula is:
  ```plaintext
  Depreciation = (Cost - Salvage) × (Remaining Life / Sum of Years' Digits)
  ```
  For a 5-year asset, the **sum of years' digits** is `5 + 4 + 3 + 2 + 1 = 15`.
- The **period** must be less than or equal to the **life**, and all inputs should be positive numbers.
- The **salvage value** must be lower than the **cost**; otherwise, depreciation won't occur.

> **Tips**:
> - Use `SYD` for calculating accelerated depreciation when you need to reflect an asset's higher usage or rapid
    obsolescence in earlier years.
> - Combine with financial forecasting tools to budget for asset replacement or tax benefits.
> - Keep in mind that depreciation spreads the cost of assets over their useful life but does not reflect actual market
    value.