<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# ACCRINTM Function

The `ACCRINTM` function in Excel is used to calculate the **interest accrued at maturity for a security** that pays
interest at maturity. This function is primarily useful in financial analysis and tracking investments that earn
interest over a fixed term and pay out that interest at the maturity date.

## Key Features of `ACCRINTM`:

- Calculates interest accrued over the full term of a security that pays interest at maturity.
- Helps determine the total interest to be earned on fixed-income investments.
- Can handle securities with various day count conventions.

## Syntax:

```plaintext
ACCRINTM(issue, maturity, rate, par, [basis])
```

- **issue**: The issue date of the security (start date when interest begins to accrue).
- **maturity**: The maturity date of the security (end date when the total interest and principal are due).
- **rate**: The annual interest rate of the security.
- **par**: The par value (face value) of the security. Defaults to `1,000` if omitted.
- **[basis]**: (Optional) Specifies the day count basis to use. Defaults to `0`. The options are:
    - `0` = US (NASD) 30/360 (default).
    - `1` = Actual/actual.
    - `2` = Actual/360.
    - `3` = Actual/365.
    - `4` = European 30/360.

## How `ACCRINTM` Works:

1. It calculates the interest accrued over the full term of a security from the **issue date** to the **maturity date**.
2. Determines the interest using the **rate**, the **par value**, and the selected **basis**.
3. Provides a result representing the total interest due on the maturity date.

## Examples:

### 1. Calculate Accrued Interest with Default Basis:

```excel
=ACCRINTM(DATE(2023,1,1), DATE(2024,1,1), 0.05, 1000)
```

**Result:** Returns the interest accrued at 5% annual interest over 1 year for a security with a par value of $1,000,
using the default 30/360 day count method.

### 2. Calculate Accrued Interest with Actual/Actual Basis:

```excel
=ACCRINTM(DATE(2023,3,1), DATE(2024,3,1), 0.06, 1500, 1)
```

**Result:** Calculates accrued interest at 6% on a par value of $1,500 using the **actual/actual** day count convention.

### 3. Accrued Interest for Less Than One Year:

```excel
=ACCRINTM(DATE(2023,6,1), DATE(2023,12,1), 0.04, 2000, 3)
```

**Result:** Calculates accrued interest over 6 months at a 4% annual rate for a $2,000 par value, following the *
*actual/365** basis.

## Notes:

- If any of the input values for **issue**, **maturity**, **rate**, or **par** are invalid, Excel will return a
  `#VALUE!` error.
- Ensure that the **issue date** is earlier than the **maturity date**, or Excel will return a `#NUM!` error.
- The choice of **basis** can significantly affect the interest calculation, especially for long-term securities.

## Applications:

- **Investment Tracking**: Easily calculate the total interest due upon the maturity of bonds or other securities.
- **Fixed-Income Portfolio Analysis**: Helps in projecting income from securities with maturity-based interest payouts.
- **Corporate Financial Management**: Useful for cash flow forecasting and tracking interest earned on long-term
  deposits.

> **Tip:** Double-check all input parameters (especially dates and interest rates) to ensure calculations align with
financial expectations and practices.