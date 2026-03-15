<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# DB Function

The `DB` function in Excel calculates the **depreciation of an asset** for a specified period using the *
*fixed-declining balance method**. This function is commonly used in accounting and asset management to determine the
depreciation expenses for an asset over time.

## Key Features of DB:

- Returns the depreciation expense for a specified period.
- Uses the fixed-declining balance method, which applies a constant depreciation rate to the remaining book value of the
  asset.
- More depreciation is allocated in earlier periods compared to later ones, making it useful for assets that lose value
  quickly in the initial years.

## Syntax:

```plaintext
DB(cost, salvage, life, period, [month])
```

- **cost**: The initial cost of the asset.
- **salvage**: The value of the asset at the end of its useful life.
- **life**: The total number of periods (usually years) over which the asset will be depreciated.
- **period**: The period for which you want to calculate depreciation (must be between 1 and the asset's life).
- **[month]** (optional): The number of months in the first year of depreciation. Defaults to `12` if omitted.

## How It Works:

1. The function calculates the depreciation for the specified period by applying the fixed-declining balance formula.
2. The **salvage value** ensures that the asset's value never depreciates below this amount, even at the end of its
   useful life.
3. If the specified **period** is within the first year, the `[month]` parameter affects the depreciation amount by
   prorating it for the number of months provided.

## Examples:

### 1. Depreciation for the 1st Year of an Asset:

```excel
=DB(10000, 1000, 5, 1)
```

**Result:** Returns the depreciation expense for the first year of an asset with an initial cost
of $10,000, a salvage value of $1,000, and a useful life of 5 years.

### 2. Depreciation for the 3rd Year with Prorated First Year:

```excel
=DB(10000, 2000, 10, 3, 6)
```

**Result:** Calculates the depreciation expense for the 3rd year of an asset with an initial cost
of $10,000, salvage value of $2,000, 10 years of life, and 6 months in the first year.

### 3. Depreciation in the Middle of the Useful Life:

```excel
=DB(15000, 3000, 7, 4)
```

**Result:** Computes the depreciation for the 4th year of a $15,000 asset with a $3,000 salvage value and a 7-year
useful life.

## Notes:

- The **life** and **period** parameters must use the same units (e.g., both in years or both in months).
- The function calculates depreciation using a declining percentage, which varies based on the asset's lifetime and the
  chosen method.
- If invalid inputs are provided, Excel may return a `#NUM!` or `#VALUE!` error. For example:
    - **Negative values** for `cost`, `salvage`, `life`, or `period` are not allowed.
    - Providing a `period` that exceeds `life` will result in an error.

## Applications:

- **Financial Reporting**: Helps in preparing depreciation schedules for accounting purposes.
- **Asset Valuation**: Useful for tracking the declining book value of an asset over time.
- **Cash Flow Analysis**: Provides insights into depreciation expenses that affect taxable income and net cash flow.

> **Tip:** Ensure that all parameters are calculated or provided in the correct units to avoid errors in your
calculations.