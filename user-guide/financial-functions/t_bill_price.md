<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

## TBILLPRICE Function

The `TBILLPRICE` function in Excel calculates the **price per $100 face value** for a Treasury bill (T-bill) based on
its discount rate. This is useful for understanding the purchase price of T-bills in financial markets.

### Key Features of TBILLPRICE:

- Computes the T-bill price as a percentage of its face value.
- Assumes a 360-day year for calculation purposes.
- Ideal for determining the cost of purchasing T-bills at a discount.

### Syntax:

```plaintext
TBILLPRICE(settlement, maturity, discount)
```

- **settlement**: The settlement date of the T-bill (the date the investor buys the bill).  
  This must be a valid Excel date.
- **maturity**: The maturity date of the T-bill (the date the bill is redeemed).  
  This must also be a valid Excel date later than the settlement date.
- **discount**: The discount rate of the T-bill (expressed as a decimal or percentage).

### Examples:

1. **Basic T-Bill Price**:
   `=TBILLPRICE(DATE(2023, 1, 1), DATE(2023, 7, 1), 0.05)`  
   Calculates the price
   per $100 face value for a T-bill with a discount rate of 5%, purchased on January 1, 2023, and redeemed on July 1, 2023.  
   **Result**: `97.50` (this means the T-bill costs $97.50 for every $100 face value).

2. **T-Bill with Higher Discount Rate**:
   `=TBILLPRICE(DATE(2023, 5, 1), DATE(2023, 11, 1), 0.07)`  
   Determines the price per $100 face value for a T-bill with a 7% discount rate, purchased on May 1, 2023, and maturing
   on November 1, 2023.  
   **Result**: `96.50`.

3. **Shorter Term T-Bill**:
   `=TBILLPRICE(DATE(2023, 8, 1), DATE(2023, 9, 1), 0.03)`  
   Calculates the price per $100 face value for a 1-month T-bill with a 3% discount rate, purchased on August 1, 2023.  
   **Result**: `99.75`.

### Notes:

- The formula for the T-bill price is based on the discount rate and length of the T-bill's term:
  ```plaintext
  TBILLPRICE = 100 × (1 − (Discount Rate × Days to Maturity / 360))
  ```
  Where **Days to Maturity** is the difference in days between **maturity** and **settlement**.
- Both **settlement** and **maturity** dates must be valid Excel dates within the same calendar year.
- The **maturity date** must always be later than the **settlement date**.

> **Tips**:
> - Use `TBILLPRICE` to calculate the upfront cost of purchasing T-bills in financial markets.
> - Make sure inputs for **discount** and **dates** are correctly formatted in Excel to avoid errors.
> - T-bills are an excellent low-risk investment option, and knowing their price helps in managing short-term liquidity.