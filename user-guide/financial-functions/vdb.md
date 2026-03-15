<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## VDB Function

The `VDB` (Variable Declining Balance) function in Excel calculates **depreciation for an asset** using the variable
declining balance method. This depreciation method is often used for assets that lose more value in the earlier years of
their lifespan, such as vehicles or machinery.

### Key Features of VDB:

- Provides greater flexibility by allowing you to switch to straight-line depreciation when it is more beneficial.
- Useful for scenarios where you need precise depreciation calculations across specific periods.
- Aids in financial reporting and tax calculations by accurately reflecting asset value over time.

### Syntax:

```plaintext
VDB(cost, salvage, life, start_period, end_period, [factor], [no_switch])
```

- **cost**: The initial cost of the asset.
- **salvage**: The value of the asset at the end of its useful life (also known as residual value).
- **life**: The total number of periods (e.g., years or months) over which the asset is expected to be used.
- **start_period**: The period at which depreciation starts.
- **end_period**: The period at which depreciation ends.
- **[factor]**: (Optional) The rate of depreciation. If omitted, Excel uses the default value of `2` (double declining
  balance).
- **[no_switch]**: (Optional) A logical value (TRUE/FALSE) that specifies whether to stop switching to straight-line
  depreciation.  
  By default, Excel switches to straight-line depreciation when it provides greater depreciation.

### Examples:

1. **Basic Variable Declining Balance Depreciation**:
   `=VDB(10000, 2000, 5, 0, 1)`  
   Calculates the depreciation of an asset costing $10,000 with a salvage value of $2,000, over a useful life of 5
   years. Depreciation is calculated for the first year.  
   **Result**: `$3,200`.

2. **Depreciation for a Specific Period**:
   `=VDB(10000, 2000, 5, 1, 2)`  
   Calculates the depreciation for the asset during the second year of its life.  
   **Result**: `$1,920`.

3. **Using a Custom Factor**:
   `=VDB(10000, 2000, 5, 0, 1, 1.5)`  
   Uses 1.5 as the depreciation factor instead of the default 2 (double declining balance), for the first year.  
   **Result**: `$2,400`.

4. **No Switching to Straight-Line**:
   `=VDB(10000, 2000, 5, 0, 1, 2, TRUE)`  
   Prevents Excel from switching to straight-line depreciation and keeps using the declining balance method.  
   **Result**: `$3,200`.

### Notes:

- The `VDB` function allows more flexibility than other depreciation functions like `DB` (Declining Balance) or `DDB` (
  Double Declining Balance).
- Switching to straight-line depreciation ensures the asset is fully depreciated by the end of its life.
- Depreciation is calculated using this formula in the declining balance method:

  ```plaintext
  Depreciation = (Remaining Book Value × Factor) / Useful Life
  ```

  If straight-line depreciation becomes greater than declining balance, Excel automatically switches unless instructed
  not to (`no_switch = TRUE`).

> **Tips**:
> - Use `VDB` for detailed and flexible depreciation calculations.
> - Ensure the input parameters, especially periods and life, align with your reporting needs.
> - Combining declining balance and straight-line methods can provide a realistic estimate of asset value over time.